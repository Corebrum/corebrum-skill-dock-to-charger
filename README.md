# Dock To Charger — OpenNav docking skill

Marketplace package for the `dock_to_charger` capability (`external_ros_node` → OpenNav `DockRobot`).

```bash
npx agenticros skills install @agenticros/dock-to-charger
# or: chrismatthieu/dock-to-charger
```

AgenticROS does **not** launch the docking server. Bring up [OpenNav docking](https://github.com/open-navigation/opennav_docking) (or a compatible `DockRobot` action server) on the robot, then install this skill.

## Mission example

```json
{
  "mission": {
    "name": "return to charger",
    "steps": [
      {
        "id": "dock",
        "capability": "dock_to_charger",
        "inputs": {
          "goal": { "dock_id": "home_charger" }
        },
        "retry": { "max_attempts": 2, "backoff_ms": 1000 }
      }
    ]
  }
}
```

If your action goal uses a different field layout, pass the full `goal` object your server expects. A bare `dock_id` string is passed through as `{ dock_id }` when no `goal` is set.

## Requirements

- OpenNav docking (or compatible) advertising `dock_robot` (`opennav_docking_msgs/action/DockRobot`)
- Transport with action support
- Dock poses configured on the robot
