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
ms.openlocfilehash: a731dc49556a73c585c6201a80ea3ea77c15cb11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124415"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="868ee-102">Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="868ee-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="868ee-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikaci můžete nasadit z většiny webových serverů, pokud jsou nakonfigurované odpovídající typy MIME (Multipurpose Internet Mail Extensions).</span><span class="sxs-lookup"><span data-stu-id="868ee-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="868ee-104">Ve výchozím nastavení je Microsoft Internetová informační služba (IIS) 7,0 nakonfigurovaný s těmito typy MIME, ale Microsoft Internetová informační služba (IIS) 5,0 a Microsoft Internetová informační služba (IIS) 6,0 nejsou.</span><span class="sxs-lookup"><span data-stu-id="868ee-104">By default, Microsoft Internet Information Services (IIS) 7.0 is configured with these MIME types, but Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 are not.</span></span>

<span data-ttu-id="868ee-105">Toto téma popisuje, jak nakonfigurovat Microsoft Internetová informační služba (IIS) 5,0 a Microsoft Internetová informační služba (IIS) 6,0 pro nasazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="868ee-105">This topic describes how to configure Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="868ee-106">Můžete kontrolovat řetězec *userAgent* v registru, abyste zjistili, zda je systém .NET Framework nainstalován.</span><span class="sxs-lookup"><span data-stu-id="868ee-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="868ee-107">Podrobnosti a skript, který projde řetězec *userAgent* k určení, zda je v systému nainstalovaná .NET Framework, najdete v tématu [zjištění, zda je nainstalovaná .NET Framework 3,0](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="868ee-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="868ee-108">Úprava nastavení vypršení platnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="868ee-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="868ee-109">Nastavení vypršení platnosti obsahu byste měli upravit na 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="868ee-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="868ee-110">Následující postup popisuje, jak to provést se službou IIS.</span><span class="sxs-lookup"><span data-stu-id="868ee-110">The following procedure outlines how to do this with IIS.</span></span>

1. <span data-ttu-id="868ee-111">Klikněte na nabídku **Start** , přejděte na **Nástroje pro správu**a klikněte na **Správce služby Internetová informační služba (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="868ee-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="868ee-112">Tuto aplikaci můžete také spustit z příkazového řádku pomocí příkazu "%SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="868ee-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="868ee-113">Rozbalte strom služby IIS, dokud nenajdete **výchozí** uzel webu.</span><span class="sxs-lookup"><span data-stu-id="868ee-113">Expand the IIS tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="868ee-114">Klikněte pravým tlačítkem na **výchozí web** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="868ee-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="868ee-115">Vyberte kartu **hlavičky protokolu HTTP** a klikněte na Povolit vypršení platnosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="868ee-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="868ee-116">Nastavte, aby platnost obsahu vypršela po 1 minutách.</span><span class="sxs-lookup"><span data-stu-id="868ee-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="868ee-117">Registrace typů MIME a přípon souborů</span><span class="sxs-lookup"><span data-stu-id="868ee-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="868ee-118">Je nutné zaregistrovat několik typů MIME a přípon souborů, aby prohlížeč v systému klienta mohl načíst správnou obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="868ee-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="868ee-119">Je nutné přidat následující typy:</span><span class="sxs-lookup"><span data-stu-id="868ee-119">You need to add the following types:</span></span>

|<span data-ttu-id="868ee-120">klapk</span><span class="sxs-lookup"><span data-stu-id="868ee-120">Extension</span></span>|<span data-ttu-id="868ee-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="868ee-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="868ee-122">. manifest</span><span class="sxs-lookup"><span data-stu-id="868ee-122">.manifest</span></span>|<span data-ttu-id="868ee-123">Aplikace/manifest</span><span class="sxs-lookup"><span data-stu-id="868ee-123">application/manifest</span></span>|
|<span data-ttu-id="868ee-124">. XAML</span><span class="sxs-lookup"><span data-stu-id="868ee-124">.xaml</span></span>|<span data-ttu-id="868ee-125">Application/XAML + XML</span><span class="sxs-lookup"><span data-stu-id="868ee-125">application/xaml+xml</span></span>|
|<span data-ttu-id="868ee-126">. Application</span><span class="sxs-lookup"><span data-stu-id="868ee-126">.application</span></span>|<span data-ttu-id="868ee-127">aplikace/x-MS-aplikace</span><span class="sxs-lookup"><span data-stu-id="868ee-127">application/x-ms-application</span></span>|
|<span data-ttu-id="868ee-128">. XBAP</span><span class="sxs-lookup"><span data-stu-id="868ee-128">.xbap</span></span>|<span data-ttu-id="868ee-129">aplikace/x-MS-XBAP</span><span class="sxs-lookup"><span data-stu-id="868ee-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="868ee-130">. deploy</span><span class="sxs-lookup"><span data-stu-id="868ee-130">.deploy</span></span>|<span data-ttu-id="868ee-131">aplikace/oktet – Stream</span><span class="sxs-lookup"><span data-stu-id="868ee-131">application/octet-stream</span></span>|
|<span data-ttu-id="868ee-132">. XPS</span><span class="sxs-lookup"><span data-stu-id="868ee-132">.xps</span></span>|<span data-ttu-id="868ee-133">application/vnd. MS-XpsDocument</span><span class="sxs-lookup"><span data-stu-id="868ee-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="868ee-134">V klientských systémech nemusíte registrovat typy MIME ani přípony souborů.</span><span class="sxs-lookup"><span data-stu-id="868ee-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="868ee-135">Jsou zaregistrovány automaticky při instalaci aplikace Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="868ee-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="868ee-136">Následující ukázka jazyka VBScript (Microsoft Visual Basic Scripting Edition) automaticky přidá nezbytné typy MIME do služby IIS.</span><span class="sxs-lookup"><span data-stu-id="868ee-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to IIS.</span></span> <span data-ttu-id="868ee-137">Chcete-li použít skript, zkopírujte kód do souboru. vbs na vašem serveru.</span><span class="sxs-lookup"><span data-stu-id="868ee-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="868ee-138">Potom spusťte skript spuštěním souboru z příkazového řádku nebo Poklikáním na soubor v Průzkumníkovi Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="868ee-138">Then, run the script by running the file from the command line or double-clicking the file in Microsoft Windows Explorer.</span></span>

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
> <span data-ttu-id="868ee-139">Spuštění tohoto skriptu několikrát vytvoří více položek mapování MIME v metabázi Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="868ee-139">Running this script multiple times creates multiple MIME map entries in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

<span data-ttu-id="868ee-140">Po spuštění tohoto skriptu nesmíte zobrazit další typy MIME z Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0 Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="868ee-140">After you have run this script, you may not see additional MIME types from the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 Microsoft Management Console (MMC).</span></span> <span data-ttu-id="868ee-141">Tyto typy MIME se ale přidaly do metabáze Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="868ee-141">However, these MIME types have been added to the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span> <span data-ttu-id="868ee-142">Následující skript zobrazí všechny typy MIME v metabázi Microsoft Internetová informační služba (IIS) 5,0 nebo Microsoft Internetová informační služba (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="868ee-142">The following script will display all the MIME types in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

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

<span data-ttu-id="868ee-143">Uložte skript jako soubor `.vbs` (například `DiscoverIISMimeTypes.vbs`) a spusťte ho z příkazového řádku pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="868ee-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
