Here’s a detailed guide for installing Aiken-lang v1.1.5 on Linux, along with solutions for common installation issues.

---

### Step-by-Step Installation Guide for Aiken v1.1.5

#### 1. **Set Up Prerequisites**

   - **Install Rust**:
     - Open a terminal and run the following command to install Rust via `rustup`:
       ```bash
       curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
       ```
     - Follow the prompts, then add Rust to your PATH by sourcing the setup file:
       ```bash
       source $HOME/.cargo/env
       ```
     - **Verify Rust**:
       ```bash
       rustc --version
       cargo --version
       ```

   - **Install Git** (if not already installed):
     - Most Linux distributions come with Git, but you can install it manually:
       ```bash
       sudo apt update
       sudo apt install git
       ```
     - **Verify Git**:
       ```bash
       git --version
       ```

   - **Install Node.js** (if required for additional tooling):
     - Install Node.js and npm with:
       ```bash
       sudo apt install nodejs npm
       ```
     - **Verify Node.js**:
       ```bash
       node -v
       npm -v
       ```

#### 2. **Clone the Aiken Repository**

   - **Clone the Repository**:
     ```bash
     git clone https://github.com/aiken-lang/aiken.git
     ```
   - **Checkout v1.1.5**:
     ```bash
     cd aiken
     git checkout v1.1.5
     ```

#### 3. **Build and Install Aiken v1.1.5**

   - **Build the Project**:
     ```bash
     cargo build --release
     ```
   - **Install Aiken Globally**:
     - To install Aiken globally, run:
       ```bash
       cargo install --path .
       ```
   - **Verify the Installation**:
     ```bash
     aiken --version
     ```

---

### Common Issues and Solutions

#### 1. **Rust or Cargo Not Recognized**

   - **Problem**: After installation, the `rustc` or `cargo` commands aren’t recognized.
   - **Solution**:
     - Ensure Rust is added to your PATH:
       ```bash
       source $HOME/.cargo/env
       ```
     - To make this permanent, add the line to your shell’s config file (e.g., `.bashrc` or `.zshrc`):
       ```bash
       echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
       source ~/.bashrc
       ```
     - **Verify**:
       ```bash
       rustc --version
       cargo --version
       ```

#### 2. **Missing Dependencies During Cargo Build**

   - **Problem**: `cargo build --release` fails due to missing dependencies.
   - **Solution**:
     - Update Rust and Cargo to the latest versions:
       ```bash
       rustup update
       ```
     - Check and resolve any dependency issues by running:
       ```bash
       cargo check
       ```

#### 3. **Build Errors During `cargo install`**

   - **Problem**: `cargo install --path .` fails due to permission issues or environment conflicts.
   - **Solution**:
     - **Check Permissions**: If you encounter permissions issues, try installing with elevated permissions:
       ```bash
       sudo cargo install --path .
       ```
     - **Clean Cargo Cache**: Sometimes clearing the Cargo cache helps:
       ```bash
       cargo clean
       ```

#### 4. **Aiken Not Recognized After Installation**

   - **Problem**: After successful installation, the `aiken` command is not recognized.
   - **Solution**:
     - Verify that `cargo` binaries are in your PATH:
       ```bash
       echo $PATH
       ```
     - If `$HOME/.cargo/bin` isn’t listed, add it manually:
       ```bash
       echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
       source ~/.bashrc
       ```

#### 5. **Linux-Specific Issues**

   - **Dependencies**: Some Linux distributions may require additional development tools.
     - For Debian-based distributions (like Ubuntu), install build-essential packages:
       ```bash
       sudo apt install build-essential
       ```
     - For Red Hat-based distributions, install the developer tools:
       ```bash
       sudo yum groupinstall 'Development Tools'
       ```

#### 6. **Permissions and Access Rights**

   - **Problem**: Permission errors when writing to `/usr/local/bin` or other protected directories.
   - **Solution**:
     - Run commands with `sudo` if writing to system directories:
       ```bash
       sudo cargo install --path .
       ```
     - Alternatively, install Cargo and Rust in a user directory and add it to PATH to avoid permissions issues.

---

If you encounter a specific error message, please share it, and I can provide more focused assistance.