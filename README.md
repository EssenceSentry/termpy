# termpy

`termpy` is a Python library designed to facilitate the execution and interaction with shell commands from Python applications. It supports both synchronous and asynchronous execution, utilizes pseudo-terminals for enhanced command interaction, and allows for custom output handling. This library is particularly valuable for applications requiring complex or dynamic command line interactions.

## Features

- **Pseudo-Terminal Support**: Execute commands within a pseudo-terminal, supporting programs that need a TTY.
- **Asynchronous Execution**: Perform command execution asynchronously, enabling non-blocking operations within your application.
- **Custom Output Handling**: Implement custom functions to process the output and errors from command executions dynamically.
- **Context Management**: Use Python's context management to ensure proper cleanup and management of terminal sessions.
- **Interactive Input Handlers**: Handle different types of user inputs (e.g., text, passwords, selections) through specialized input handler classes.
- **Color and Escape Code Utilities**: Utilize built-in utilities for managing color output and simulating keyboard inputs using escape codes.

## Why Choose `termpy` for Your Command Execution Needs?

### Enhanced Control and Flexibility

`termpy` goes beyond basic command execution by providing advanced features such as pseudo-terminal support and asynchronous execution. This makes it an ideal choice for developers who need precise control over command line interactions within their Python applications. Whether it's running background processes, interacting with command-line tools that require a TTY, or handling complex user input scenarios, `termpy` offers the capabilities you need.

### Streamlined Interaction with Command Line Interfaces

With `termpy`, interacting with command line interfaces becomes more intuitive and automated. The library's support for detecting and handling different types of input (like passwords or selection inputs) can greatly simplify the development of applications that interact with secure or complex CLI tools. For instance, automating tasks in a setup script or creating a user-friendly wrapper around a command-line tool can be achieved with minimal hassle.

### Custom Output Handling

`termpy` allows you to define custom output handlers, enabling you to process and react to the output from commands dynamically. This is especially useful for applications that need to parse command output and make decisions or trigger further actions based on that data. Whether it's monitoring the progress of a command, extracting specific data from the output, or implementing custom logging solutions, `termpy` gives you the tools to do it effectively.

### Simplified Development of Cross-Platform Tools

For developers working on cross-platform applications, maintaining consistency in command execution across different environments can be challenging. `termpy` helps mitigate these issues by abstracting the complexities of platform-specific behaviors, especially in handling terminal interactions. This makes it easier to develop tools that work seamlessly on multiple operating systems.

### Robustness and Reliability

The built-in utilities for managing color output and simulating keyboard inputs using escape codes enhance the robustness and user experience of command-line applications. These features allow developers to create more interactive and user-friendly CLI tools without compromising on reliability or performance.

### Use Case Scenario

Consider a scenario where a system administrator needs to automate the setup of software across multiple machines. Using `termpy`, they can create a script that not only installs the software but also configures it interactively based on the outputs and required inputs, handling any user prompts automatically. This reduces manual intervention and streamlines the deployment process.

## Installation

Clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/termpy.git
```

Change to the project directory:

```bash
cd termpy
```

It's recommended to use a virtual environment:

```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

Install the library:

```bash
python setup.py install
```

## Usage

Here's a simple example of using `termpy` to execute a command asynchronously with a pseudo-terminal:

```python
from termpy.executor import ShellCommandExecutor
from termpy.interactive_response import InputSelector, PasswordInputHandler
from termpy.utils import cprint

# Define a custom output handler
def custom_output_handler(terminal, output):
    input_selector = InputSelector(terminal)
    assert isinstance(input_selector.input_handler, PasswordInputHandler)
    input_selector.input(password)
    # We can discard the output if we want, or print it or anything
    assert terminal.read_output() == "Hello, World!"
    cprint("Worked as expected!", color="green")
    

# Create an executor with PTY support and asynchronous mode
executor = ShellCommandExecutor(use_pty=True, output_handler=custom_output_handler)

# Run a command
executor.run('sudo echo "Hello, World!"')
```

## Contributing

Contributions are welcome!

## License

This is free and unencumbered software released into the public domain. See [LICENSE](LICENSE) for more information.
