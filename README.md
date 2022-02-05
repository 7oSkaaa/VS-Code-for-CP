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

4.  **Install Code Runner on VS CODE**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install formulahendry.code-runner
```

5.  **Change Settings of Code Runner**

- Open `Settings` in vscode (ctrl + comma)
- Search on `Run Code Configuration`
  - [x] on `Clear Previous Output`
  - [x] on `Run In Terminal`
  - [x] on `Save All Files Before Run`
- Don't Close `Settings` because we will use it in the next step

6.  **Change Executor Map of Code Runner**
-   Click on `Edit in settings json` at `Executor Map By File Extension`
-   at `code-runner.executorMap` edit in cpp label
-   choose one flag from these and put it in cpp label:
    - this flag for execute the file with cp flags and make the code terminate after one second
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG $fileName -o $fileNameWithoutExt && timeout -k 0 1s $dir$fileNameWithoutExt"`
    - this flag for execute the file with cp flags only
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"` 
    - this flag for execute the file with cp flags but less debuger than the above one
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o "%e" "%f" -O2 -Wno-unused-result $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"` 

6.  **Use Files instead of terminal**
- We will use freopen and files txt to take input and output from use instead of terminal
- First we should put this function in our code
```C++
void Fast_IO(){
    ios_base::sync_with_stdio(false), cin.tie(nullptr), cout.tie(nullptr);
    #ifndef ONLINE_JUDGE
        freopen("input.txt", "r", stdin), freopen("output.txt", "w", stdout); 
    #endif
}
```
- Create text file and name it `input.txt`
