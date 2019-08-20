---
title: 'Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 3a9bf79a9d505fef53b62cb589920adcf95ae92a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611501"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Aplikaci můžete nasadit z většiny webových serverů, pokud jsou nakonfigurované odpovídající typy MIME (Multipurpose Internet Mail Extensions). Ve výchozím nastavení je Microsoft Internetová informační služba (IIS) 7,0 nakonfigurovaný s těmito typy MIME, ale Microsoft Internetová informační služba (IIS) 5,0 a Microsoft Internetová informační služba (IIS) 6,0 nejsou.

Toto téma popisuje, jak nakonfigurovat Microsoft Internetová informační služba (IIS) 5,0 a Microsoft Internetová informační služba (IIS) 6,0 pro nasazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.

> [!NOTE]
> Můžete kontrolovat řetězec *userAgent* v registru, abyste zjistili, zda je systém .NET Framework nainstalován. Podrobnosti a skript, který projde řetězec *userAgent* k určení, zda je v systému nainstalovaná .NET Framework, najdete v tématu [zjištění, zda je nainstalovaná .NET Framework 3,0](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Úprava nastavení vypršení platnosti obsahu

Nastavení vypršení platnosti obsahu byste měli upravit na 1 minutu. Následující postup popisuje, jak to provést se službou IIS.

1. Klikněte na nabídku **Start** , přejděte na **Nástroje pro správu**a klikněte na **Správce služby Internetová informační služba (IIS)** . Tuto aplikaci můžete také spustit z příkazového řádku pomocí příkazu "%SystemRoot%\system32\inetsrv\iis.msc".

2. Rozbalte strom služby IIS, dokud nenajdete **výchozí** uzel webu.

3. Klikněte pravým tlačítkem na **výchozí web** a v místní nabídce vyberte **vlastnosti** .

4. Vyberte kartu **hlavičky protokolu HTTP** a klikněte na Povolit vypršení platnosti obsahu.

5. Nastavte, aby platnost obsahu vypršela po 1 minutách.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>Registrace typů MIME a přípon souborů

Je nutné zaregistrovat několik typů MIME a přípon souborů, aby prohlížeč v systému klienta mohl načíst správnou obslužnou rutinu. Je nutné přidat následující typy:

|Linka|Typ MIME|
|---------------|---------------|
|.manifest|Aplikace/manifest|
|. XAML|Application/XAML + XML|
|. Application|aplikace/x-MS-aplikace|
|.xbap|application/x-ms-xbap|
|. deploy|aplikace/oktet – Stream|
|. XPS|application/vnd.ms-xpsdocument|

> [!NOTE]
> V klientských systémech nemusíte registrovat typy MIME ani přípony souborů. Jsou zaregistrovány automaticky při instalaci aplikace Microsoft .NET Framework.

Následující ukázka jazyka VBScript (Microsoft Visual Basic Scripting Edition) automaticky přidá nezbytné typy MIME do služby IIS. Chcete-li použít skript, zkopírujte kód do souboru. vbs na vašem serveru. Potom spusťte skript spuštěním souboru z příkazového řádku nebo Poklikáním na soubor v [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> Spuštění tohoto skriptu několikrát vytvoří více položek mapování MIME v metabázi Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0.

Po spuštění tohoto skriptu nesmíte zobrazit další typy MIME z Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0 Microsoft Management Console (MMC). Tyto typy MIME se ale přidaly do metabáze Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0. Následující skript zobrazí všechny typy MIME v metabázi Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0.

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

Uložte skript jako `.vbs` soubor ( `DiscoverIISMimeTypes.vbs`například) a spusťte ho z příkazového řádku pomocí následujícího příkazu:

```console
cscript DiscoverIISMimeTypes.vbs
```
