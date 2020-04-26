# Ubuntu Desktop Shortcut
- create **postman.desktop** in **~/.local/share/applications/**
- `**nano postman.desktop**` :
```bash
[Desktop Entry]
Version=1.0
Name=Postman
Comment=Postman Desktop
Exec=/home/<your-username>/<path-to-postman-executable>
Path=/home/<your-username>/<path-to-postman-executable-directory>
Icon=/home/<your-username>/<path-to-postman-logo>
Terminal=false
Type=Application
Categories=Development;
```
- Verify the file : **`desktop-file-validate postman.desktop`**
- Run : **`sudo update-desktop-database`**
