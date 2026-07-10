# ISIR-EXTENDER

ISIR-EXTENDER is a modular ROS 2 robotics stack for assistive robot control,
teleoperation, shared-control research, and fast controller prototyping.

The project is developed at
[ISIR](https://www.isir.upmc.fr/) (Institut des Systemes Intelligents et de
Robotique, Sorbonne Universite / CNRS) around a robot-agnostic controller
architecture. It supports experiments on several robot platforms through shared
interfaces, reusable ROS 2 controllers, operator input backends, and web-based
supervision tools.

<p align="center">
  <img alt="ROS 2" src="https://img.shields.io/badge/ROS%202-Humble-22314e?style=for-the-badge" />
  <img alt="Ubuntu" src="https://img.shields.io/badge/Ubuntu-22.04-e95420?style=for-the-badge&logo=ubuntu&logoColor=white" />
  <img alt="C++" src="https://img.shields.io/badge/C%2B%2B-17-00599c?style=for-the-badge&logo=cplusplus&logoColor=white" />
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10-3776ab?style=for-the-badge&logo=python&logoColor=white" />
  <img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-5-3178c6?style=for-the-badge&logo=typescript&logoColor=white" />
  <img alt="Core ROS packages: MIT" src="https://img.shields.io/badge/core%20ROS%20packages-MIT-7f987f?style=for-the-badge" />
</p>

<p align="center">
  <a href="#repositories">Repositories</a> |
  <a href="#project-map">Project Map</a> |
  <a href="#robots-in-use">Robots In Use</a> |
  <a href="#architecture">Architecture</a> |
  <a href="#controllers-and-control-modes">Controllers And Control Modes</a> |
  <a href="#quick-start">Quick Start</a> |
  <a href="#how-to">How To</a> |
  <a href="#maintainers-and-contributors">Maintainers And Contributors</a> |
  <a href="#team-onboarding">Team Onboarding</a> |
  <a href="#contributing">Contributing</a> |
  <a href="#active-work">Active Work</a> |
  <a href="#open-source-and-licensing">Open Source And Licensing</a> |
  <a href="#bloom-migration">Bloom Migration</a>
</p>

## Repositories

Fast links to the main ISIR-EXTENDER repositories:

| Repository | Quick description |
| --- | --- |
| [`extender_workspace`](https://github.com/ISIR-EXTENDER/extender_workspace) | Start here. Workspace manifest, build guide, uv environment, and onboarding entry point. |
| [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces) | Robot abstraction layer, shared command/state interfaces, and kinematics boundary. |
| [`controllers`](https://github.com/ISIR-EXTENDER/controllers) | ROS 2 controllers for velocity, position, impedance/shared-control workflows, and Sandbox prototyping. |
| [`input_interfaces`](https://github.com/ISIR-EXTENDER/input_interfaces) | Joystick, SpaceMouse, tablet backend, and websocket-to-ROS routing packages. |
| [`extender_ui`](https://github.com/ISIR-EXTENDER/extender_ui) | Current React tablet UI, screen builder, Sandbox V0.0, visual-servoing screens, and operator workflows. |
| [`tools`](https://github.com/ISIR-EXTENDER/tools) | Shared messages and tools, including `extender_msgs`, `apriltag_detector`, and media helpers. |
| [`visual_servoing`](https://github.com/ISIR-EXTENDER/visual_servoing) | Visual-servoing control loop and AprilTag-based experiments. |
| [`explorer_stack`](https://github.com/ISIR-EXTENDER/explorer_stack) | Explorer robot hardware, simulation, descriptions, and robot-specific tooling. |
| [`qontrol_controller`](https://github.com/ISIR-EXTENDER/qontrol_controller) | QP-solver-based controller work for Explorer-related experiments. |
| [`hub`](https://github.com/ISIR-EXTENDER/hub) | Hub and digital output integration. |
| [`bloom`](https://github.com/ISIR-EXTENDER/bloom) | WIP future monorepo for the UI/backend platform. |

## Current State

- The main integration workspace is
  [`extender_workspace`](https://github.com/ISIR-EXTENDER/extender_workspace).
- The core controller stack is built around
  [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces) and
  [`controllers`](https://github.com/ISIR-EXTENDER/controllers).
- Core ROS repositories such as `robot_interfaces`, `controllers`,
  `input_interfaces`, and `tools` are MIT-licensed.
- The recommended app for new UI/backend/controller integration is
  **Sandbox V0.0**.
- Petanque packages remain available as legacy/example workflows, but new
  development should not start from Petanque unless the task is explicitly
  Petanque maintenance.
- Visual-servoing work currently uses
  [`visual_servoing`](https://github.com/ISIR-EXTENDER/visual_servoing),
  [`tools/apriltag_detector`](https://github.com/ISIR-EXTENDER/tools), and the
  Sandbox V0.0 visual-servoing screens.
- The same architecture is used across Explorer, Kinova Gen3, and Franka FR3
  experiments.
- Ubuntu 22.04 and ROS 2 Humble are the documented baseline.
- Ubuntu 24.04 and the next ROS 2 upgrade are an active migration target, but
  they are not yet the reference setup.

## Project Map

License values below reflect the root `LICENSE` files visible in the current
repositories.

| Repository | Role | License |
| --- | --- | --- |
| [`extender_workspace`](https://github.com/ISIR-EXTENDER/extender_workspace) | Main ROS 2 workspace manifest, build guide, shared Python environment, and onboarding entry point. | Not declared in repo root |
| [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces) | Robot abstraction layer and shared command/state interfaces used by controllers. | MIT |
| [`controllers`](https://github.com/ISIR-EXTENDER/controllers) | ROS 2 control plugins, including Cartesian velocity, joint interpolation, shared control, and `sandbox_controller`. | MIT |
| [`input_interfaces`](https://github.com/ISIR-EXTENDER/input_interfaces) | Input and backend packages, including joystick input and `tablet_interface`. | MIT |
| [`extender_ui`](https://github.com/ISIR-EXTENDER/extender_ui) | React tablet frontend, screen builder, runtime apps, Sandbox V0.0, and visual-servoing supervision screens. | Not declared in repo root |
| [`tools`](https://github.com/ISIR-EXTENDER/tools) | Shared utilities such as `extender_msgs`, `apriltag_detector`, media tools, and test publishers. | MIT |
| [`visual_servoing`](https://github.com/ISIR-EXTENDER/visual_servoing) | Visual-servoing control loop and AprilTag-based workflow used by current experiments. | Apache-2.0 |
| [`explorer_stack`](https://github.com/ISIR-EXTENDER/explorer_stack) | Explorer robot packages, simulation, hardware interface, descriptions, and robot-specific tooling. | Not declared in repo root |
| [`qontrol_controller`](https://github.com/ISIR-EXTENDER/qontrol_controller) | QP-solver-based controller integration for Explorer-related experiments. | GPL-3.0 |
| [`hub`](https://github.com/ISIR-EXTENDER/hub) | Hub and digital output integration. | Not declared in repo root |
| [`bloom`](https://github.com/ISIR-EXTENDER/bloom) | WIP next-generation monorepo for the future UI/backend platform. | MIT |

## Robots In Use

Extender is designed so the same controller and input-interface work can move
between robot platforms through `robot_interfaces`.

| Robot | Type | Current use | Main packages |
| --- | --- | --- | --- |
| Explorer | Custom assistive robotic arm | Main Extender demonstrator platform, used for assistive manipulation, teleoperation, sandbox control, Petanque legacy demos, and Explorer-specific hardware/simulation work. | [`explorer_stack`](https://github.com/ISIR-EXTENDER/explorer_stack), [`qontrol_controller`](https://github.com/ISIR-EXTENDER/qontrol_controller), [`controllers`](https://github.com/ISIR-EXTENDER/controllers), [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces) |
| Kinova Gen3 | Commercial collaborative arm | Development and validation platform for controller experiments, shared teleoperation flows, visual-servoing integration, and workflows that need a supported lab robot without Explorer-specific hardware constraints. | [`controllers`](https://github.com/ISIR-EXTENDER/controllers), [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces), [`input_interfaces`](https://github.com/ISIR-EXTENDER/input_interfaces), [`tools`](https://github.com/ISIR-EXTENDER/tools) |
| Franka FR3 | Commercial collaborative arm | Research platform for testing the same Extender controller abstractions on Franka hardware, especially when experiments need precise collaborative robot behavior. | [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces), [`controllers`](https://github.com/ISIR-EXTENDER/controllers), Franka-specific integration packages |

Explorer-related work builds on the
[Orthopus Explorer repositories](https://github.com/ORTHOPUS-EXPLORER) and the
assistive robotics expertise developed around the Orthopus project.

The goal is not to duplicate each controller for each robot. Controllers should
target the shared abstractions, and robot-specific packages should handle
hardware details, simulation details, and platform-specific configuration.

## Architecture

Extender is organized as a layered ROS 2 architecture. The important idea is
that controllers should target shared robot abstractions, while robot-specific
packages handle hardware details.

### Core Layers

| Layer | Repositories | Responsibility |
| --- | --- | --- |
| Workspace and setup | `extender_workspace` | Imports the project repositories, documents the build flow, and defines the shared Python environment. |
| Robot abstraction | `robot_interfaces` | Provides shared robot command/state interfaces so controllers can run across supported platforms. |
| Controllers | `controllers`, `qontrol_controller` | Implements velocity, position, impedance, shared-control, QP, and sandbox controller workflows. |
| Input and backend | `input_interfaces` | Converts joystick, SpaceMouse, and tablet websocket messages into ROS 2 commands and feedback. |
| Operator UI | `extender_ui` | Provides runtime screens, Sandbox V0.0, screen builder, camera/video widgets, and supervision tools. |
| Tools and perception | `tools`, `visual_servoing` | Provides shared messages, AprilTag detection, media helpers, and visual-servoing workflows. |
| Robot platforms | `explorer_stack`, robot-specific integrations | Owns hardware, simulation, descriptions, limits, and platform-specific configuration. |

### Controller-First Path

The stable control path is:

```text
robot_interfaces
  -> controllers
  -> robot integrations, tools, and input_interfaces
```

This means a controller should be written against `robot_interfaces` whenever
possible. Explorer, Kinova Gen3, and Franka FR3 should differ mostly through
robot-specific configuration and integration packages, not through duplicated
controller logic.

### Tablet And Teleoperation Path

For tablet-based operation and integration tests:

```text
operator action
  -> extender_ui widget/store
  -> websocket message
  -> input_interfaces/tablet_interface
  -> ROS 2 topic/service
  -> controller, robot interface, or perception node
  -> ROS feedback/topic snapshot
  -> tablet_interface
  -> UI state, event, or monitor widget
```

The central command topic for current teleoperation workflows is `/teleop_cmd`.
It is used by joystick, SpaceMouse, and tablet flows, with mode and velocity
information interpreted by the relevant controller.

### Sandbox Integration Path

Sandbox V0.0 is the reference app for new UI/backend/controller integration:

```text
extender_ui Sandbox V0.0
  -> tablet_interface backend
  -> sandbox_controller
  -> robot_interfaces + tools
```

Use this path before creating app-specific workflows. It gives developers a
known setup for teleoperation, visual-servoing supervision, snake control, topic
monitoring, and controller smoke tests.

## Controllers And Control Modes

The controller stack is meant to keep research algorithms portable across the
robots used in the project. The shared path is:

```text
operator input or autonomous command
  -> TeleopCommand / controller-specific command
  -> ros2_control controller
  -> robot_interfaces
  -> robot-specific hardware or simulation
```

### What Works Today

| Capability | Current state |
| --- | --- |
| Cartesian velocity control | Implemented for teleoperation workflows. Used as the main direct-control mode for joystick, SpaceMouse, tablet, and Sandbox V0.0 tests. |
| Joint position / position interpolation | Implemented for smooth point-to-point commands and basic position-control workflows. |
| Teleoperation basics | Working through `/teleop_cmd`, joystick mappings, tablet widgets, scaling, mode selection, and controller-side command handling. |
| Franka impedance control | Available for Franka workflows through Franka-specific integration and controller abstractions. |
| Kinova Gen3 impedance control | Available for Gen3 experiments through the shared architecture and robot-specific integration. |
| Perimanipulation and shared control on Franka | Working research workflow for shared-control experiments on Franka. |
| Sandbox controller | Working generic starting point for new control algorithms and UI/backend integration tests. |

### In Progress Or Needs Improvement

| Topic | Status |
| --- | --- |
| Explorer impedance control | Planned next step. The goal is to bring impedance-style behavior to Explorer while respecting its hardware constraints. |
| Perimanipulation and shared control on Explorer | Needs improvement. The Explorer stack has QP limits and hardware constraints that make direct transfer from Franka non-trivial. |
| Explorer continuous rotation constraints | Explorer does not have a slip ring, so controller behavior must account for cable/winding limits and avoid unsafe assumptions about unlimited rotation. |
| QP-limited Explorer control | `qontrol_controller` is available for Explorer-related experiments, but integration and tuning need careful validation against real hardware limits. |

### Design Rules For New Controllers

- Start from `sandbox_controller` when prototyping a new algorithm.
- Keep command contracts explicit: topic names, message types, scaling, frame
  conventions, and enable/disable behavior must be documented.
- Keep portable logic above robot-specific hardware details.
- Validate in simulation or Sandbox V0.0 before hardware tests.
- Treat Explorer constraints separately from Franka/Kinova assumptions,
  especially for QP limits, joint limits, and rotation/cable constraints.

## Quick Start

Use `extender_workspace` as the entry point when setting up a development
machine.

```bash
mkdir -p ~/workspace/extender
cd ~/workspace/extender
git clone https://github.com/ISIR-EXTENDER/extender_workspace.git
cd extender_workspace
vcs import src < extender.repos --workers 1
```

Install Python dependencies from the workspace root:

```bash
uv sync --extra ros-build --extra dev
```

Use the vision extra only for vision workflows:

```bash
uv sync --extra ros-build --extra dev --extra vision
```

Build the core robot interfaces first, then the rest of the workspace:

```bash
source /opt/ros/humble/setup.bash
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install --packages-up-to robot_interfaces
source install/setup.bash
colcon build --symlink-install
```

See the
[`extender_workspace` README](https://github.com/ISIR-EXTENDER/extender_workspace)
for the complete setup guide, uv usage, and troubleshooting notes.

## How To

### Start New Controller Work

1. Start from `controllers/sandbox_controller`.
2. Keep the controller contract compatible with `robot_interfaces`.
3. Use Sandbox V0.0 for UI/backend/controller smoke tests.
4. Build only the affected package while iterating:

```bash
colcon build --symlink-install --packages-select sandbox_controller
```

### Start New Tablet Or Backend Work

1. Use
   [`extender_ui`](https://github.com/ISIR-EXTENDER/extender_ui) for frontend
   screens and widgets.
2. Use
   [`input_interfaces/tablet_interface`](https://github.com/ISIR-EXTENDER/input_interfaces)
   for websocket-to-ROS routing.
3. Prefer Sandbox V0.0 screens for new integration work.
4. Keep shared screen/app JSON changes small and review timestamp-only noise
   before committing.

### Run The Tablet Flow

Start the backend:

```bash
cd extender_workspace/src/input_interfaces/tablet_interface
make run-node
```

Start the frontend:

```bash
cd extender_workspace/src/extender-ui
npm install
npm run dev
```

Then open the local Vite URL and choose **Sandbox V0.0**.

### Work On Visual Servoing

Use the current visual-servoing stack:

| Layer | Package |
| --- | --- |
| UI supervision | `extender_ui` Sandbox V0.0 visual-servoing screens |
| Backend bridge | `input_interfaces/tablet_interface` |
| Tag detection | `tools/apriltag_detector` |
| Control loop | `visual_servoing` |
| Robot command path | `controllers` + `robot_interfaces` |

For camera-heavy workflows, avoid using generic topic monitors for
`sensor_msgs/msg/Image` or `sensor_msgs/msg/CompressedImage`. Use stream/video
widgets or dedicated vision nodes instead.

### Add Or Update Dependencies

Python dependencies that are shared at workspace level belong in
`extender_workspace/pyproject.toml`.

```bash
uv add <package>
git diff -- pyproject.toml uv.lock
```

Commit `pyproject.toml` and `uv.lock` together.

## Maintainers And Contributors

### Maintainer

| Name | Role | GitHub | Website |
| --- | --- | --- | --- |
| Susana Sanchez Restrepo | ISIR-EXTENDER maintainer | [`@ssrpo`](https://github.com/ssrpo) | [suziesr.xyz](https://suziesr.xyz/) |
| Megane Millan | ISIR-EXTENDER maintainer | [`@MegMll`](https://github.com/MegMll) | - |

### Contributor Profiles

| Contributor | GitHub |
| --- | --- |
| Etienne Moullet | [`@emoullet`](https://github.com/emoullet) |
| Megane Millan | [`@MegMll`](https://github.com/MegMll) |
| Susana Sanchez Restrepo | [`@ssrpo`](https://github.com/ssrpo) |
| `technodroide` | [`@technodroide`](https://github.com/technodroide) |
| Walid Oubraim | [`@woubraim`](https://github.com/woubraim) |

## Team Onboarding

### 1. Join The GitHub Organization

Ask an ISIR-EXTENDER maintainer, currently
[`@ssrpo`](https://github.com/ssrpo) or
[`@MegMll`](https://github.com/MegMll), for access to the GitHub organization
and the repositories needed for your work. New contributors usually need access
to:

- `extender_workspace`
- `robot_interfaces`
- `controllers`
- `input_interfaces`
- `extender_ui`
- `tools`

Vision or robot-specific tasks may also need:

- `visual_servoing`
- `explorer_stack`
- `qontrol_controller`
- `hub`

### 2. Set Up Your Machine

Use the documented baseline first:

| Component | Current baseline |
| --- | --- |
| OS | Ubuntu 22.04 |
| ROS 2 | Humble |
| Python | 3.10 |
| Python environment | `uv` from `extender_workspace` |
| Build tool | `colcon` |

Ubuntu 24.04 and the next ROS 2 upgrade are in progress. Coordinate with the
team before using that setup as your main development environment.

### 3. Clone Through The Workspace

Do not clone random repositories into unrelated folders for integration work.
Start from `extender_workspace`, then import repositories with `vcs import`.

### 4. Choose The Right Starting Point

| Goal | Start here |
| --- | --- |
| New controller or algorithm | `controllers/sandbox_controller` |
| Robot abstraction or message contract | `robot_interfaces` |
| Tablet backend route or ROS topic bridge | `input_interfaces/tablet_interface` |
| UI widget or operator screen | `extender_ui` Sandbox V0.0 |
| AprilTag or camera detection | `tools/apriltag_detector` |
| Visual-servoing loop | `visual_servoing` |
| Explorer hardware/simulation | `explorer_stack` |

### 5. Ask For Review Early

Open a draft PR when the direction is visible, even if the work is not finished.
Small PRs are easier to test during integration weeks.

## Contributing

We try to keep the Extender repositories easy to review, easy to test, and safe
to integrate during robot development weeks. These standards apply across the
ISIR-EXTENDER organization unless a repository README documents a stricter local
rule.

### Branches And Pull Requests

- Branch from an up-to-date `main`.
- Use short, descriptive branch names:
  - `feat/snake-control-screen`
  - `fix/topic-monitor-stale-state`
  - `docs/workspace-onboarding`
- Open draft PRs early when the direction needs validation.
- Keep PRs focused on one logical change.
- Split generic infrastructure and app-specific behavior when they can be
  reviewed independently.
- Write PR titles with Conventional Commit style, for example
  `feat: add visual servoing monitor`.
- Include:
  - what changed;
  - why it changed;
  - how it was tested;
  - any robot, ROS, or hardware assumptions.

### Documentation

- Write READMEs, comments, PR descriptions, and shared project docs in English.
- Update the relevant README when adding:
  - a ROS topic or message contract;
  - a launch flow;
  - a dependency;
  - a frontend widget;
  - a new screen or app;
  - a controller behavior that operators or researchers must understand.
- Keep user-facing documentation practical: include commands, expected URLs,
  topics, and common failure modes.
- Do not document local-only agent files, private notes, or machine-specific
  paths in shared repositories.

### Code And Architecture

- Prefer shared abstractions over robot-specific duplication.
- Keep controller logic compatible with `robot_interfaces` whenever possible.
- Keep frontend runtime/page code generic unless behavior truly applies to every
  app.
- Keep app-specific frontend behavior in the app or screen configuration layer.
- Keep video/image transport separate from generic topic monitoring.
- Avoid adding new ROS message types when an existing generic message or typed
  payload contract is enough.

### Dependencies

- Workspace-level Python dependencies belong in
  `extender_workspace/pyproject.toml`.
- Commit `pyproject.toml` and `uv.lock` together.
- Do not rely on global `pip install` commands for repository dependencies.
- Document system dependencies in the relevant README when they are required for
  a build, launch file, camera, controller, or hardware interface.
- For frontend dependencies, commit both `package.json` and the lockfile.

### Testing And Validation

Choose checks that match the change. Useful examples:

```bash
git diff --check
uv lock --locked
colcon build --symlink-install --packages-select <package_name>
```

For `tablet_interface` changes:

```bash
cd src/input_interfaces/tablet_interface
make test
```

For `extender_ui` changes:

```bash
npm run lint
npm run build
```

For UI work, include screenshots when the change affects layout, operator
workflow, or robot supervision screens.

### Generated Files And Local State

Do not commit generated or local state:

- `build/`, `build.*`
- `install/`, `install.*`
- `log/`, `log.*`
- `.venv/`
- `node_modules/`
- rosbags, local logs, camera dumps, and machine-specific workspace files
- timestamp-only JSON noise such as unchanged screen `updatedAt` fields

### Robot Safety

- Treat robot-facing changes as safety-sensitive.
- Make command scaling, mode changes, enable/disable behavior, and topic names
  explicit in code and documentation.
- Prefer simulation or Sandbox V0.0 smoke tests before hardware tests.
- Keep UI states clear for operators: active modes, stale topics, failed
  subscriptions, gripper state, and visual-servoing enable state should be
  visible whenever relevant.

## Active Work

Current active directions across the organization:

| Area | Status |
| --- | --- |
| Sandbox V0.0 | Recommended integration app for new UI/backend/controller work. |
| Visual servoing | Active work around webcam/AprilTag pipelines, `apriltag_detector`, `visual_servoing`, and UI supervision screens. |
| Snake control | Active Sandbox workflow using two joystick modes and hold-to-enable snake commands. |
| Explorer impedance | Planned next controller milestone, with extra care around QP limits and hardware constraints. |
| Ubuntu 24.04 / ROS 2 upgrade | Migration target, not yet the documented baseline. |
| Bloom | WIP future monorepo for the UI/backend platform. |

## Open Source And Licensing

ISIR-EXTENDER is developed as open-source research software.

The core ROS packages are MIT-licensed:

- [`robot_interfaces`](https://github.com/ISIR-EXTENDER/robot_interfaces)
- [`controllers`](https://github.com/ISIR-EXTENDER/controllers)
- [`input_interfaces`](https://github.com/ISIR-EXTENDER/input_interfaces)
- [`tools`](https://github.com/ISIR-EXTENDER/tools)

Some repositories intentionally use different terms. For example,
`visual_servoing` is Apache-2.0, `qontrol_controller` is GPL-3.0, and Bloom is
MIT.

Several integration or application repositories do not yet declare a root
license file in this profile snapshot, including `extender_workspace`,
`extender_ui`, `explorer_stack`, and `hub`. Add an explicit `LICENSE` file before
reusing, redistributing, or packaging those repositories outside the project.
Always check each repository's current `LICENSE` file before integrating with
external projects.

## Bloom Migration

[`Bloom`](https://github.com/ISIR-EXTENDER/bloom) is the WIP next-generation
robot UI platform. It is being developed as a monorepo that will eventually
replace the current split between `extender_ui` and its backend flow.

Until Bloom supports the same robot workflows, the stable integration path
remains:

```text
extender_workspace
  -> input_interfaces/tablet_interface
  -> extender_ui Sandbox V0.0
  -> controllers + robot_interfaces
```

## Research And Credits

- **Lab**:
  [Institut des Systemes Intelligents et de Robotique](https://www.isir.upmc.fr/)
  (ISIR), Sorbonne Universite / CNRS, Paris.
- **Project**: ANR DEFI TRANSFERT project Extender, developed with Orthopus.
- **Demonstrator**: PEPR Robotics Petanque assistive robotics demonstrator.
- **Acknowledgements**: Explorer-related work builds on the Orthopus project and
  its assistive robotics expertise.
