# Butterfly-WindowsPowerShell
Settings for Windows PowerShell, including plugins : **oh-my-posh** etc..

&nbsp;
&nbsp;
****
## Native appearance (Windows 11)
> Settings: https://docs.microsoft.com/en-us/windows/terminal/customize-settings/profile-appearance
1. Open windows terminal's `settings.json`, you can set 'defaults' to apply to all of your profiles, or one of 'list'
2. Add Background or Acrylic attribute, either or
```Json
 "profiles": {
        "defaults": {
            "fontFace": "MesloLGM NF",
            "backgroundImage": "<your image path>",
            //"useAcrylic": true,
            //"acrylicOpacity": 0.7
        },
        "list": [
            {
                "commandline": "powershell.exe",
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "Windows PowerShell"
            },
            {
                "commandline": "cmd.exe",
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "\u547d\u4ee4\u63d0\u793a\u7b26"
            }
        ]
    },
```
3. Save and restart terminal
****

&nbsp;
&nbsp;
****
## Oh-my-posh v3 (Windows 11)
![image](https://github.com/butterflydreams/Butterfly-OS_WindowsTools/blob/main/oh-my-posh/Oh-my-posh.jpg)
> Usage: https://ohmyposh.dev/docs/windows
1. Open Windows Terminal
2. Input command line *__"winget install JanDeDobbeleer.OhMyPosh"__*, getting the installion dir path is `C:\Users\<user>\AppData\Local\Programs\oh-my-posh\`  ([winget?](https://docs.microsoft.com/en-us/windows/package-manager/winget/))
3. Open path dialog 'Settings' -> 'System' -> 'System info' -> 'Advanced system settings' -> 'Advanced' -> 'Environment Variables' -> 'Path', then add oh-my-posh path line *__"C:\Users\<user>\AppData\Local\Programs\oh-my-posh\bin\"__*
4. Input command line *__"$PROFILE"__*, getting the config file path is `C:\Users\<user>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`
5. Edit `$PROFILE` file(if null should create new), then add the following line *__"oh-my-posh --init --shell pwsh --config C:\Users\<user>\AppData\Local\Programs\oh-my-posh\themes\agnoster.omp.json | Invoke-Expression"__*
6. Input command line *__". $PROFILE"__*  to refresh, or restart terminal or reboot, show new effect

&nbsp;
> Fonts: https://ohmyposh.dev/docs/fonts
1. Download recommend font **"Meslo LGM NF"** , from [nerdfonts](https://www.nerdfonts.com/) or [github](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip) 
2. Install font `Meslo LG M Regular Nerd Font Complete Windows Compatible.ttf`
3. Open windows terminal's `settings.json`, add under attribute in settings file
```Json
{
    "profiles":
    {
        "defaults":
        {
          "fontFace": "MesloLGM NF",
        }
    }
}
```
4. Restart terminal, show new font

&nbsp;
> Themes: https://ohmyposh.dev/docs/themes
1. Input command, preview all themes
```Bash
Get-ChildItem -Path "~\AppData\Local\Programs\oh-my-posh\themes\*" -Include '*.omp.json' | Sort-Object Name | ForEach-Object -Process {
    $esc = [char]27
    Write-Host ""
    Write-Host "$esc[1m$($_.BaseName)$esc[0m"
    Write-Host ""
    oh-my-posh --config $($_.FullName) --pwd $PWD
    Write-Host ""
}
```
2. Select a theme name, edit `$PROFILE` file(`C:\Users\<user>\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`), modify *__"oh-my-posh --init --shell pwsh --config C:\Users\<user>\AppData\Local\Programs\oh-my-posh\themes\<your theme>.omp.json | Invoke-Expression"__*
3. Or you can add a `*.omp.json` theme file(such as [butterfly.omp.json](https://github.com/butterflydreams/Butterfly-Windows_Power_Shell/blob/main/butterfly.omp.json)) to `C:\Users\<user>\AppData\Local\Programs\oh-my-posh\themes`, then edit `$PROFILE` file to use it
4. Input command line *__". $PROFILE"__* to refresh, or restart terminal or reboot, show your theme
****

&nbsp;
&nbsp;
****
## Oh-my-zsh (Windows Subsystem for Linux 2 / WSL2 / SSH - Debian9)
![image]https://github.com/butterflydreams/Butterfly-OS_WindowsTools/blob/main/oh-my-posh/Oh-my-zsh.jpg)
> Installation: https://github.com/ohmyzsh/ohmyzsh/wiki/Installing-ZSH#ubuntu-debian--derivatives-windows-10-wsl--native-linux-kernel-with-windows-10-build-1903

> Themes: https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
****
