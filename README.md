[Yazi docs](https://yazi-rs.github.io/docs/installation)

1. Install nerd font in terminal.

2. Clone yazi config to Roaming

3. `ya pkg install` to download packages

3. Add to powershell profile
    ```ps
    function y {
        $tmp = (New-TemporaryFile).FullName
        yazi $args --cwd-file="$tmp"
        $cwd = Get-Content -Path $tmp -Encoding UTF8
        if (-not [String]::IsNullOrEmpty($cwd) -and $cwd -ne $PWD.Path) {
            Set-Location -LiteralPath (Resolve-Path -LiteralPath $cwd).Path
        }
        Remove-Item -Path $tmp
    }
    ```
