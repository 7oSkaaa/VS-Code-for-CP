# VS-Code-for-CP

For competitive programming, I use Linux dual booted alongside Windows. My favorite IDE is VS Code and it's perfect for short codes in CP.

1.  **Install C++**

```
sudo apt install g++
```

2.  **Instal VS Code**

```
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
rm -f packages.microsoft.gpg
```
```
sudo apt install apt-transport-https
sudo apt update
sudo apt install code # or code-insiders
```

3.  **Install C++ on VS CODE**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install ms-vscode.cpptools-extension-pack
```
