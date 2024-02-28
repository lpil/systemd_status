# systemd_status

Inspect the status of running systemd units.

[![Package Version](https://img.shields.io/hexpm/v/systemd_status)](https://hex.pm/packages/systemd_status)
[![Hex Docs](https://img.shields.io/badge/hex-docs-ffaff3)](https://hexdocs.pm/systemd_status/)

```sh
gleam add systemd_status
```
```gleam
import systemd_status

// In this example we're also using the shellout package
import shellout

pub fn main() {
  let #(command, arguments) = systemd_status.unit_property_list_command("my-service")
  let assert Ok(output) = shellout.command(command, arguments, in: ".", opt: [])
  let assert Ok(service) = systemd_status.parse_service(output)
  service
  // Service(
  //   id: "my-service.service",
  //   type_: SimpleService,
  //   load_state: Loaded,
  //   active_state: Active,
  //   sub_state: "running",
  //   result: "success",
  //   main_pid: Some(3_764_255),
  //   description: Some("Super cool important service"),
  //   state_change_timestamp: Some("Tue 2024-02-27 22:50:37 UTC"),
  //   active_enter_timestamp: Some("Tue 2024-02-27 22:50:37 UTC"),
  //   active_exit_timestamp: Some("Tue 2024-02-27 22:50:37 UTC"),
  //   inactive_enter_timestamp: Some("Tue 2024-02-27 22:50:37 UTC"),
  //   inactive_exit_timestamp: Some("Tue 2024-02-27 22:50:37 UTC"),
  // )
}
```

Further documentation can be found at <https://hexdocs.pm/systemd_status>.
