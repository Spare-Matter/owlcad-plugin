# OwlCAD

The `owlcad` MCP server builds and edits parametric 3D CAD models for 3D printing. All units are
millimeters and the Z axis points up.

- Run `evaluate` after building a model, and `print_check` before calling a part printable.
- Save work with `save_project` and give the user the `open_in_editor` link, so they can open
  the project at owlcad.com and change any dimension.
- For STEP, call `export_step`, then poll `job_status` until it finishes.
- Read `owlcad://schema/primitives` and `owlcad://schema/conventions` with `read_resource`
  before building, and `owlcad://printers` for printer ids.
