# Uyarı
Sisteminize olacaklar için sorumluluk almıyorum. Sizin riskiniz.

# Windows10Debloater

Script/Utility/Application to debloat Windows 10

#  Windows10Debloater.ps1 ve Windows10DebloaterGUI.ps1 dosyalarını Nasıl Çalıştırabilirsiniz

Aşağıda PowerShell scriptlerini çalıştırabilmek için farklı methotlar vardır. Yöntemler şunlardır:

İlk Yöntem:

1) Github ana sayfasından .zip dosyasını indirin ve istediğiniz klasöre .zip dosyasını çıkartın.
2) Çıkarttıktan sonra, PowerShell'i (ya da PowerShell ISE) yönetici olarak açın.
3) PowerShell düzenlemeyi akitfleştirin.
<code>Set-ExecutionPolicy Unrestricted -Force</code>
4) Bittiğinde, dosyaları nereye çıkarttıysanız orayı seçin:
  örneğin - `cd c:\temp`
5) Sonra, komut dosyasını çalıştırabilmek için, yandaki kodu yazınız:
   `.\Windows10DebloaterGUI.ps1`

İkinci Yöntem:

1) Github ana sayfasından .zip dosyasını indirin ve istediğinz klasöre .zip dosyasını çıkartın.
2) Çalıştırmak istediğiniz PowerShell dosyasına sağ tıklayın and "PowerShell İle Çalıştır"a tıklayın.
3) Bunlar üstteki adımlar olmadan scripti çalıştırmak için izin verir fakat PowerShell script'i çalıştırmak istediğinizden emin misiniz diye soracaktır.

Unutmayın, bu scripti düzgünce çalıştırabilmek için yönetici olarak çalıştırmak gereklidir.


# Windows10SysPrepDebloater.ps1 Dosyasını Nasıl Çalıştırabilirsiniz

WindowsSysPrepDebloater.ps1 dosyası için, hangi işlevleri kullanıldığını belirtmek için burada birkaç parametre var. Bu parametreler:
`-SysPrep, -Debloat`. 

Parametreleri çalıştırmak için, sonrasında:

1) Github ana sayfasından .zip dosyasını indirin ve istediğinz klasöre .zip dosyasını çıkartın.
2) Çıkarttıktan sonra, PowerShell'i (ya da PowerShell ISE) yönetici olarak açın.
3) Bittiğinde, dosyaları nereye çıkarttıysanız orayı seçin:
  örneğin - `cd c:\temp`
4) Sonra, komut dosyasını çalıştırabilmek için, yandaki kodu yazınız:
  e.g. - `.\Windows10SysPrepDebloater.ps1 -Sysprep, -Debloat -Privacy`


# Sysprep, Interactive, ve GUI Uygulaması

There are now 3 versions of my Windows10Debloater - There is an interactive version, a GUI app version, and a pure silent version.

Windows10SysPrepDebloater.ps1 - The silent version now utilizes the switch parameters: -Sysprep, -Debloat -Privacy. The silent version can be useful for deploying MDT Images/sysprepping or any other way you deploy Windows 10. This will work to remove the bloatware during the deployment process.

Windows10Debloater.ps1 - This interactive version is what it implies - a Windows10Debloater script with interactive prompts. This one should not be used for deployments that require a silent script with optional parameters. This script gives you choices with prompts as it runs so that you can make the choices of what the script does.

Windows10DebloaterGUI.ps1 There is now a GUI Application named Windows10DebloaterGUI.ps1 with buttons to perform all of the functions that the scripts do. This is better for the average user who does not want to work with code, or if you'd prefer to just see an application screen. 

# Switch Parameters

There are 3 switch parameters in the Windows10SysPrepDebloater.ps1 script.

The first one is -SysPrep, which runs the command within a function: get-appxpackage | remove-appxpackage. This is useful since some administrators need that command to run first in order for machines to be able to properly provision the apps for removal.

The second switch parameter is -Debloat, which does as it suggests. It runs the following functions: Start-Debloat, Remove-Keys, and Protect-Privacy.

Remove-Keys removes registry keys leftover that are associated with the bloatware apps listed above, but not removed during the Start-Debloat function.

Third, Protect-Privacy adds and/or changes registry keys to stop some telemetry functions, stops Cortana from being used as your Search Index, disables "unneccessary" scheduled tasks, and more.

# This script will remove the bloatware from Windows 10 when using Remove-AppXPackage/Remove-AppXProvisionedPackage, and then delete specific registry keys that are were not removed beforehand. For best results, this script should be ran before a user profile is configured, otherwise you will likely see that apps that should have been removed will remain, and if they are removed you will find broken tiles on the start menu.

These registry keys are:

EclipseManager,
ActiproSoftwareLLC,
Microsoft.PPIProjection,
Microsoft.XboxGameCallableUI

You can choose to either 'Debloat' or 'Revert'. Depending on your choice, either one will run specific code to either debloat your Windows 10 machine.

The Debloat switch choice runs the following functions:

Debloat,
Remove-Keys,
Protect-Privacy,
Stop-EdgePDF (If chosen)

The Revert switch choice runs the following functions:

Revert-Changes,
Enable-EdgePDF

The Revert option reinstalls the bloatware and changes your registry keys back to default. 

# The scheduled tasks that are disabled are:

XblGameSaveTaskLogon,
XblGameSaveTask,
Consolidator,
UsbCeip,
DmClient

These scheduled tasks that are disabled have absolutely no impact on the function of the OS.

# Bloatware that is removed:

3DBuilder,
ActiproSoftware,
Alarms,
Appconnector,
Asphalt8,
Autodesk SketchBook,
Bing Finance,
Bing Food And Drink,
Bing Health And Fitness,
Bing News,
Bing Sports,
Bing Travel,
Bing Weather,
BioEnrollment,
Camera,
CandyCrush,
CandyCrushSoda,
Caesars Slots Free Casino,
ContactSupport,
CyberLink MediaSuite Essentials,
DrawboardPDF,
Duolingo,
EclipseManager,
Facebook,
FarmVille 2 Country Escape,
Flipboard,
Fresh Paint,
Get started,
iHeartRadio,
King apps,
Maps,
March of Empires,
Messaging,
Microsoft Office Hub,
Microsoft Solitaire Collection,
Microsoft Sticky Notes,
Minecraft,
Netflix,
Network Speed Test,
NYT Crossword,
Office Sway,
OneNote,
OneConnect,
Pandora,
People,
Phone,
Phototastic Collage,
PicsArt-PhotoStudio,
PowerBI,
Royal Revolt 2,
Shazam,
Skype for Desktop,
SoundRecorder,
TuneInRadio,
Twitter,
Windows communications apps,
Windows Feedback,
Windows Feedback Hub,
Windows Reading List,
XboxApp,
Xbox Game CallableUI,
Xbox Identity Provider,
Zune Music,
Zune Video.

# Quick download link

`iex ((New-Object System.Net.WebClient).DownloadString('https://git.io/debloat'))`

# Credits

Thank you to a60wattfish, abulgatz, xsisbest, Damian, Vikingat-RAGE, and Reddit user /u/GavinEke for some of the suggestions and fixes that I have placed into my scripts. You all have done a fantastic job!
