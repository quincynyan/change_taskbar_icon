# change_taskbar_icon

Referenced from https://stackoverflow.com/questions/70413031/change-the-taskbar-icon-for-windows-store-apps

> Buddy do I have good news for you, I was in the same boat as you, looking for the same deleted post, and just managed to figure it out.
>
> Start by creating this script with any name (for example AppIdScript), just make sure the extension is .ps1
>
> ```powershell
> $installedapps = get-AppxPackage
>
>
> foreach ($app in $installedapps)
> {
>     foreach ($id in (Get-AppxPackageManifest $app).package.applications.application.id)
>     {
>
>         $line = $app.Name + " = " + $app.packagefamilyname + "!" + $id
>         echo $line
>
>     }
> }
> Start-Sleep -Seconds 10
> ```
>
> Then save, right click and run with powershell.
>
> You can also run this command in a command prompt, the results are similar.
>
> ```batch
> reg query HKEY_CURRENT_USER\Software\Classes\ /s /f AppUserModelID | find "REG_SZ"
> ```
>
> Next copy the output of the script to a txt file (so you can Ctrl+F and search for app names in it).
>
> Once you've found the app you want to change the icon for, copy its App ID (usually starting with "Microsoft."), then right click on your desktop, create new shortcut, and paste in
>
> ```batch
> explorer.exe shell:appsFolder\PasteAppIDHere
> ```
>
> and click Next.
>
> Now you have a shortcut with the File Explorer icon, so right click and go to properties, click Change Icon..., and select the .ico file you want to replace it with. Apply the changes and click OK.
>
> Once that's done, open a new command prompt window, drag and drop in the "Win7AppId1.1.exe" file (if you no longer have it here's the download link) into the prompt, then press space, then drag in the shortcut you just created, the press space, then paste the App ID, then press enter.
>
> For example the creation of the shortcut for the Xbox App looked like this for me:
>
> ```batch
> "C:\Users\MYNAME\Desktop\Win7AppId1.1.exe" C:\Users\MYNAME\Desktop\Xbox.lnk Microsoft.GamingApp_8wekyb3d8bbwe!Microsoft.Xbox.App
> ```
>
> Once you're done, you should be able to put the shortcut on your taskbar and the icon should stay the same.
>
> Hope this helps!

## [2021-10-12] []: # Path: README.md

# Windows Terminal
