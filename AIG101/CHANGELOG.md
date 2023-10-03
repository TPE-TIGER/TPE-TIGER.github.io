# API version release notes
## V1.1.0 (2023-10)
The functionality and changes below were added in AIG-101 V1.1.0.

### New
#### Tag Access (Taghub)
- Direct read / write method by tag
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Taghub | Access | `GET /tags/access/{provider}/{source}/{tag}` | Direct read method by tag |
    | Taghub | Access | `PUT /tags/access/{provider}/{source}/{tag}` | Direct write method by tag |
