# Week 3 - Part A: Data Inventory

## 1. Dataset Overview

| Item                | Description                                                                                             |
| ------------------- | ------------------------------------------------------------------------------------------------------- |
| Dataset             | SpaceNet 8 - Germany Training Public                                                                    |
| Source              | SpaceNet public AWS S3 bucket                                                                           |
| Source path         | `s3://spacenet-dataset/spacenet/SN8_floods/tarballs/Germany_Training_Public.tar.gz`                     |
| Geographic coverage | Germany                                                                                                 |
| Purpose             | Flood-affected road and building assessment using satellite imagery and geospatial annotations          |
| Data formats        | GeoTIFF (`.tif`), GeoJSON (`.geojson`), CSV (`.csv`)                                                      |
| Storage location    | `data/raw/spacenet8/`                                                                                   |
| Dataset version     | Germany Training Public archive (2022 release)                                                          |
| Data provider       | SpaceNet                                                                                                |
| Access              | Publicly downloadable via AWS S3                                                                        |
| Usage rights        | License and attribution requirements to be verified against the official SpaceNet dataset documentation |

## 2. Data Inventory

| Data Component         | Format  | File Count | Purpose                                                                      |
| ---------------------- | ------- | ---------- | ---------------------------------------------------------------------------- |
| Pre-event imagery      | GeoTIFF | 202        | Satellite imagery before the event                                           |
| Post-event imagery     | GeoTIFF | 282        | Satellite imagery after the event                                            |
| Geospatial annotations | GeoJSON | 202        | Infrastructure geometries and attributes                                     |
| Label-image mapping    | CSV     | 1          | Associates annotations with pre-event and post-event images                  |
| Reference metadata     | CSV     | 1          | Infrastructure objects, flood labels, geometry references, and road metadata |
| Original archive       | TAR.GZ  | 1          | Original downloaded dataset package                                          |
| **Total**              |         | **689**    |                                                                              |

## 3. Data Inspection Evidence

### 3.1 Satellite Imagery

Two sample GeoTIFF images were inspected using Rasterio.

| Property                    | Pre-event Sample                | Post-event Sample               |
| --------------------------- | ------------------------------- | ------------------------------- |
| File                        | `10500500C4DD7000_0_15_63.tif` | `1040050035DC3B00_0_15_63.tif` |
| Dimensions                  | 1300 × 1300                     | 1743 × 1742                     |
| Bands                       | 3                               | 3                               |
| Data type                   | uint8                           | uint8                           |
| Coordinate reference system | EPSG:4326                       | EPSG:4326                       |
| Resolution                  | 3.743 × 10⁻⁶ degrees/pixel      | 2.794 × 10⁻⁶ degrees/pixel      |
| NoData value                | 255                             | None                            |

The inspected images have different dimensions and spatial resolutions. Geospatial alignment must be considered before pixel-level comparison or joint model processing.

### 3.2 GeoJSON Annotations

Inspected file: `annotations/0_15_63.geojson`

- GeoJSON type: `FeatureCollection`
- Total features: 20
- LineString geometries: 7 (Linear geometries such as road footprints)
- Polygon geometries: 13 (Building footprints)
- Observed properties include `id`, `building`, `flooded`, `highway`, `lanes`, `surface`, `image_id`, and `location`.

The annotations contain geospatial infrastructure features. Geometry types and attributes must be considered together when identifying buildings and roads.

### 3.3 Label-Image Mapping

File: `Germany_Training_Public_label_image_mapping.csv`

- Records: 202
- Columns: 4
- Missing values in `post-event image 2`: 122
- Mapping records with one post-event image: 122
- Mapping records with two post-event images: 80

File existence checks confirmed:

| Validation                                    | Result  |
| --------------------------------------------- | ------- |
| Existing annotation references                | 202/202 |
| Existing pre-event image references           | 202/202 |
| Existing post-event image mappings            | 202/202 |
| Total mapped post-event images                | 282     |
| Mapping records with missing referenced files | 0       |

The missing second post-event image values reflect optional image associations rather than broken file references.

### 3.4 Reference Metadata

File: `Germany_Training_Public_reference.csv`

- Records: 9,761
- Columns: 6
- Columns: `ImageId`, `Object`, `Wkt_Pix`, `Flooded`, `length_m`, `travel_time_s`

**Infrastructure records**

| Object   | Count |
| -------- | ----- |
| Road     | 5,702 |
| Building | 4,059 |

**Flood status records**

| Flooded | Count |
| ------- | ----- |
| False   | 7,183 |
| True    | 2,498 |
| Null    | 80    |

The 80 `Null` flood labels require explicit handling during subsequent preparation and evaluation.

## 4. Relevance to Project Requirements

| Data Need                             | Dataset Component                      | Justification                                                                            |
| ------------------------------------- | -------------------------------------- | ---------------------------------------------------------------------------------------- |
| Pre-event and post-event observations | PRE-event and POST-event GeoTIFF files | Support image-based comparison of potentially flood-affected areas                       |
| Road and building information         | GeoJSON annotations and reference CSV | Provide infrastructure geometries and reference information                              |
| Dataset traceability                  | Mapping and reference CSV files        | Preserve relationships between satellite images, annotations, and infrastructure records |

*Requirement IDs (FR/NFR/RAI) will be added after verification against the Week 2 requirements document.*

## 5. Data Quality and Limitations

1. **Spatial alignment:** Pre-event and post-event images may have different dimensions, resolutions, and pixel grids. Geospatial alignment must be addressed before pixel-level comparison.
2. **Missing flood labels:** The reference CSV contains 80 `Null` flood-status values. These must not be treated automatically as non-flooded examples.
3. **Multiple post-event images:** Some image-label mappings contain two post-event images. Their relationships must be preserved during processing.
4. **Geographic transferability:** The inspected training subset covers Germany. Model performance on Malaysian flood conditions cannot be assumed without additional evaluation.
5. **Data rights:** Dataset usage and redistribution conditions must be verified before publishing data or derived artifacts.
6. **Validation scope:** The current checks confirm file readability for selected examples and file existence for mapped records. They do not yet establish the integrity, annotation accuracy, or geospatial alignment of every image.

## 6. Inspection Tools

- Python
- Jupyter Notebook in Visual Studio Code
- pathlib
- pandas
- Rasterio
- json

Inspection notebook: `notebooks/week3_pipeline.ipynb`

## 7. Data Handling Decision

The raw SpaceNet 8 dataset will remain unchanged in `data/raw/spacenet8/`.

Subsequent pipeline stages will write prepared outputs to `data/processed/` while preserving image identifiers, annotation relationships, and geospatial metadata.

Raw dataset files are excluded from Git tracking using `.gitignore`.