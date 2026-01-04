# Data Model: Local Image Support

## Entities

### ImageAsset

- **Description**: A local image referenced by a documentation page.
- **Fields**:
  - `source_page`: Identifier or path of the documentation page that references the image.
  - `relative_path`: Project-relative path as written in the source content.
  - `resolved_path`: Normalized absolute or canonical path within the project.
  - `alt_text`: Optional alt text or caption from the source content.
  - `format`: Detected file format (e.g., jpg, png).
  - `status`: One of `resolved`, `missing`, `blocked`.
  - `size_bytes`: File size when resolved.
- **Validation Rules**:
  - `relative_path` must not escape the project root.
  - `status` is `missing` when the resolved file does not exist.
  - `status` is `blocked` when the path violates safety constraints.

### DocumentationPage

- **Description**: A generated documentation page that may reference images.
- **Fields**:
  - `source_path`: Path to the source document.
  - `output_path`: Path to the generated output.
  - `image_assets`: Collection of associated `ImageAsset` references.

## Relationships

- **DocumentationPage** 1 → N **ImageAsset** (a page references many images).
