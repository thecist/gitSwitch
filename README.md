# GitSwitch

**GitSwitch** is a rudimentary yet functional Python script designed to manage multiple Git user profiles on a single machine. It allows you to switch between different GitHub identities effortlessly, making it ideal for developers who need to work with multiple Git accounts. This tool was created with simplicity in mind, storing only the minimal necessary data to avoid dependency on unimportant files or excessive metadata.

## Features

- **Create and Manage Multiple Git Profiles**: Store separate SSH keys and Git configurations for each user in dedicated folders.
- **Switch Between Users**: Quickly change Git profiles by updating your SSH and Git configurations with a simple command.
- **Minimalistic Design**: No unnecessary files or metadata are stored in memory. If a folder contains more than one SSH key pair (`id_blablabla` and `id_blablabla.pub`), the script will notify you to manually manage them.
- **Non-Intrusive Configuration**: Deleting a Git configuration does not break the system; it simply leaves you with a blank configuration.

## How It Works

1. **Create a User Profile**: 
    - Generate SSH keys and store them along with a basic Git configuration in a dedicated folder.
    - If a folder with the same email already exists, you'll be prompted to manage the existing files before proceeding.

2. **Switch Between Users**:
    - The script will update the SSH config and Git configuration based on the selected profile.
    - If multiple SSH keys are found, it will archive the existing keys and notify you to manually manage them.

3. **Archive Old SSH Keys**: 
    - When generating new SSH keys, any existing keys will be archived to prevent conflicts.

## Installation

To use GitSwitch, simply download the script and run it with Python:

```bash
python gitswitch.py
```

Make sure to make the script executable:

```bash
chmod +x gitswitch.py
```

## Usage

```bash
./gitswitch.py create_user -email your_email@example.com -name "Your Name"
./gitswitch.py switch your_email@example.com
./gitswitch.py regenerate_ssh -email your_email@example.com
```

### Commands

- **create_user**: Creates a new Git user profile with a unique SSH key.
    - `-email`: Your email associated with the Git profile (required).
    - `-name`: The global username for the Git account.
    - `-key_type`: Type of SSH key (default is `ed25519`).
    - `-passphrase`: Optional passphrase for SSH key security.

- **switch**: Switches to a different Git user profile based on the provided email.
    - `email`: The email associated with the Git profile you want to switch to.

- **regenerate_ssh**: Generates new SSH keys for the specified user.
    - `-email`: Your email associated with the Git profile (required).
    - `-key_type`: Type of SSH key (default is `ed25519`).
    - `-passphrase`: Optional passphrase for SSH key security.

## Notes

- This tool is in its early stages and should be used with caution. It works just enough to help you start managing your Git identities without much overhead.
- If you encounter issues with multiple SSH keys, you'll need to manually handle them. Consider reading an article on managing multiple SSH keys, which will be linked here in the future.
- I plan to improve this code over time as I continue to use it. Your feedback is appreciated and will help guide future enhancements.

### TODO

- **Extend Support for Additional Hosts:** Implement functionality to allow SSH configurations for multiple hosts, not just `github.com`.
  
- **Enhance User Switching Logic with Regex:** Refactor the user-switching mechanism to utilize regular expressions for more robust and flexible pattern matching.
  
- **Integrate Comprehensive Error Handling:** Add thorough error handling throughout the code to ensure graceful handling of unexpected situations and to improve the overall reliability of the script.
  
- **Develop Unit Tests for Core Functions:** Write and implement unit tests for all key functions to ensure correctness and facilitate future maintenance.

## License

This project is open-source and available under the MIT License.
