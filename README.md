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
sudo apt install code
```

3.  **Install C++ on VS CODE**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install ms-vscode.cpptools-extension-pack
```

4.  **Install C/C++ Compile Run**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install danielpinto8zz6.c-cpp-compile-run
```

5.  **Install Code Runner on VS CODE**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install formulahendry.code-runner
```

6.  **Change Settings of Code Runner**

- Open `Settings` in vscode (ctrl + comma)
- Search on `Run Code Configuration`
  - [x] on `Clear Previous Output`
  - [x] on `Run In Terminal`
  - [x] on `Save All Files Before Run`
- Don't Close `Settings` because we will use it in the next step

7.  **Change Executor Map of Code Runner**
-   Click on `Edit in settings json` at `Executor Map By File Extension`
-   at `code-runner.executorMap` edit in cpp label
-   choose one flag from these and put it in cpp label:
    - this flag for execute the file with cp flags and make the code terminate after one second
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG $fileName -o $fileNameWithoutExt && timeout -k 0 1s $dir$fileNameWithoutExt"`
    - this flag for execute the file with cp flags only
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"` 
    - this flag for execute the file with cp flags but less debuger than the above one
      - `"cd $dir && g++ -std=c++17 -Wshadow -Wall -o "%e" "%f" -O2 -Wno-unused-result $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"` 
    - this flag for Windows
      - `"cd $dir && g++ $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"` 

8.  **Use Files instead of terminal**
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

9.  **Split Screen to make the view better for you
- The image in below will show you the view after splitting it.
  - ![Screenshot from 2022-02-05 21-00-34](https://user-images.githubusercontent.com/63050133/152655170-89857fb7-4f8a-4425-9f54-55503d8d4b62.png)


**Enjoy now with you CP Enviroment**


----

<br><br><br>

## Optional things to do

**Install Atom One Dark Theme**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install akamud.vscode-theme-onedark
```

**Install Bracket Pair Colorizer**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install CoenraadS.bracket-pair-colorizer
```

**Install Easy icon theme**

- Launch VS Code Quick Open (Ctrl+P), paste the following command, and press enter.

```
ext install jamesmaj.easy-icons
```


**Make Your Snippet**

- You can go to [this site](https://snippet-generator.app/) and make a snippet for you

- After that you can copy the snippet and insert it in your vscode to call it in anytime

<br><br><br>

### You can use my template for competitve programming with cpp from [here](https://github.com/7oSkaaa/VS-Code-for-CP/blob/main/Template.cpp)

<br><br><br>

<hr>

### This is my settings.json file if you want to use it

```json
{
    "workbench.colorTheme": "One Dark",
    "workbench.iconTheme": "vscode-icons",
    "workbench.editorAssociations": {
        "*.ipynb": "jupyter.notebook.ipynb",
        "*.html": "default"
    },
    "files.autoSave": "onFocusChange",
    "files.associations": {
        "random": "cpp",
        "*.tcc": "cpp",
        "deque": "cpp",
        "list": "cpp",
        "string": "cpp",
        "unordered_map": "cpp",
        "unordered_set": "cpp",
        "vector": "cpp"
    },
    "editor.mouseWheelZoom": true,
    "files.autoGuessEncoding": true,
    "debug.terminal.clearBeforeReusing": true,
    "task.problemMatchers.neverPrompt": false,
    "gnuGlobal.debugMode": "Enabled",
    "gnuGlobal.autoUpdate": "Enabled",
    "c-cpp-compile-run.run-in-external-terminal": true,
    "code-runner.clearPreviousOutput": true,
    "code-runner.runInTerminal": true,
    "code-runner.saveAllFilesBeforeRun": true,
    "code-runner.saveFileBeforeRun": true,
    "code-runner.languageIdToFileExtensionMap": {
        "bat": ".bat",
        "powershell": ".ps1",
        "typescript": ".ts"
    },
    "tasks": [
        {
            "label": "build main.cpp",
            "type": "shell",
            "command": "/usr/bin/g++",
            "args": [
                "-g",
                "-Wall",
                "-Wextra",
                "-Wshadow",
                "-Wformat=2",
                "-Wfloat-equal",
                "-o",
                "main",
                "main.cpp",
                "-DAKP"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ],
    "diffEditor.wordWrap": "off",
    "editor.codeLens": false,
    "editor.accessibilitySupport": "off",
    "editor.suggestSelection": "first",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "python.autoComplete.addBrackets": true,
    "python.globalModuleInstallation": true,
    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "name": "One Dark italic",
                "scope": [
                    "comment",
                    "entity.other.attribute-name",
                    "keyword",
                    "markup.underline.link",
                    "storage.modifier",
                    "storage.type",
                    "string.url",
                    "variable.language.super",
                    "variable.language.this"
                ],
                "settings": {
                    "fontStyle": "italic"
                }
            },
            {
                "name": "One Dark italic reset",
                "scope": [
                    "keyword.operator",
                    "keyword.other.type",
                    "storage.modifier.import",
                    "storage.modifier.package",
                    "storage.type.built-in",
                    "storage.type.function.arrow",
                    "storage.type.generic",
                    "storage.type.java",
                    "storage.type.primitive"
                ],
                "settings": {
                    "fontStyle": ""
                }
            }
        ]
    },
    "code-runner.executorMap": {
        "javascript": "node",
        "java": "cd $dir && javac $fileName && java $fileNameWithoutExt",
        "c": "cd $dir && gcc $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "cpp": "cd $dir && g++ -std=c++17 -Wshadow -Wall -o -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG $fileName -o $fileNameWithoutExt && timeout -k 0 1s $dir$fileNameWithoutExt",
        "objective-c": "cd $dir && gcc -framework Cocoa $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "php": "php",
        "python": "python3 -u",
        "perl": "perl",
        "perl6": "perl6",
        "ruby": "ruby",
        "go": "go run",
        "lua": "lua",
        "groovy": "groovy",
        "powershell": "powershell -ExecutionPolicy ByPass -File",
        "bat": "cmd /c",
        "shellscript": "bash",
        "fsharp": "fsi",
        "csharp": "scriptcs",
        "vbscript": "cscript //Nologo",
        "typescript": "ts-node",
        "coffeescript": "coffee",
        "scala": "scala",
        "swift": "swift",
        "julia": "julia",
        "crystal": "crystal",
        "ocaml": "ocaml",
        "r": "Rscript",
        "applescript": "osascript",
        "clojure": "lein exec",
        "haxe": "haxe --cwd $dirWithoutTrailingSlash --run $fileNameWithoutExt",
        "rust": "cd $dir && rustc $fileName && $dir$fileNameWithoutExt",
        "racket": "racket",
        "scheme": "csi -script",
        "ahk": "autohotkey",
        "autoit": "autoit3",
        "dart": "dart",
        "pascal": "cd $dir && fpc $fileName && $dir$fileNameWithoutExt",
        "d": "cd $dir && dmd $fileName && $dir$fileNameWithoutExt",
        "haskell": "runhaskell",
        "nim": "nim compile --verbosity:0 --hints:off --run",
        "lisp": "sbcl --script",
        "kit": "kitc --run",
        "v": "v run",
        "sass": "sass --style expanded",
        "scss": "scss --style expanded",
        "less": "cd $dir && lessc $fileName $fileNameWithoutExt.css",
        "FortranFreeForm": "cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "fortran-modern": "cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "fortran_fixed-form": "cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "fortran": "cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt"
      },
    "editor.renderWhitespace": "none",
    "editor.minimap.enabled": false,
    "breadcrumbs.enabled": false,
    "editor.wordWrap": "on",
    "editor.inlineHints.enabled": false,
    "editor.linkedEditing": true,
    "scm.alwaysShowActions": true,
    "C_Cpp.vcFormat.indent.preserveWithinParentheses": true,
    "C_Cpp.vcFormat.newLine.beforeWhileInDoWhile": true,
    "C_Cpp.vcFormat.newLine.closeBraceSameLine.emptyFunction": true,
    "C_Cpp.vcFormat.newLine.closeBraceSameLine.emptyType": true,
    "C_Cpp.vcFormat.newLine.scopeBracesOnSeparateLines": true,
    "C_Cpp.vcFormat.newLine.beforeOpenBrace.type": "newLine",
    "C_Cpp.vcFormat.indent.withinParentheses": "alignToParenthesis",
    "C_Cpp.vcFormat.newLine.beforeOpenBrace.block": "newLine",
    "C_Cpp.vcFormat.newLine.beforeOpenBrace.function": "newLine",
    "C_Cpp.vcFormat.newLine.beforeOpenBrace.lambda": "newLine",
    "C_Cpp.vcFormat.newLine.beforeOpenBrace.namespace": "newLine",
    "C_Cpp.vcFormat.wrap.preserveBlocks": "allOneLineScopes",
    "C_Cpp.vcFormat.indent.braces": true,
    "C_Cpp.vcFormat.indent.caseContentsWhenBlock": true,
    "C_Cpp.vcFormat.indent.caseLabels": true,
    "C_Cpp.vcFormat.indent.preserveComments": true,
    "[cpp]": {
        "editor.defaultFormatter": "xoanis.clion-formatter"
    },
    "editor.fontFamily": "'Fira Code', 'fedora', 'Droid Sans Mono', 'monospace', monospace, 'Droid Sans Fallback'",
    "terminal.integrated.fontFamily": "monospace",
    "editor.fontLigatures": true,
    "editor.codeLensFontFamily": "Fira Code",
    "editor.defaultFormatter": "danielpinto8zz6.c-cpp-compile-run",
    "C_Cpp.default.cppStandard": "c++20",
    "C_Cpp.default.compileCommands": "g++ -std=c++17 -Wshadow -Wall -o \"%e\" \"%f\" -g -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG",
    "C_Cpp.default.cStandard": "c17",
    "explorer.confirmDelete": false,
    "shareCode.pastebin.username": "7oSkaaa",
    "python.analysis.completeFunctionParens": true,
    "python.defaultInterpreterPath": "python3",
    "code-runner.temporaryFileName": "temp_file",
    "python.pythonPath": "python3",
    "command": "python3",
    "jupyter.askForKernelRestart": false,
    "workbench.settings.openDefaultSettings": true,
    "markdown-preview-enhanced.previewTheme": "one-dark.css",
    "vsicons.dontShowNewVersionMessage": true,
    "files.exclude": {
        "**/.classpath": true,
        "**/.project": true,
        "**/.settings": true,
        "**/.factorypath": true
    },
    "scm.inputFontFamily": "Fira Code",
    "bracketPairColorizer.depreciation-notice": false,
    "[django-html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "editor.unicodeHighlight.nonBasicASCII": false,
    "C_Cpp.autocompleteAddParentheses": true,
    "terminal.integrated.copyOnSelection": true,
    "files.participants.timeout": 1500,
    "explorer.confirmDragAndDrop": false,
    "diffEditor.ignoreTrimWhitespace": false,
    "workbench.editor.enablePreview": false,
    "git.autofetch": true,
    "gitlens.advanced.messages": {
        "suppressGitMissingWarning": true
    },
}
```
