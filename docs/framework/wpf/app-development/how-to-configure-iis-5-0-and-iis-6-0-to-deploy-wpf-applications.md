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
ms.openlocfilehash: 3179679abcf32e40374c7f02e64466a326a73195
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013013"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="2376a-102">Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="2376a-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="2376a-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Aplikaci můžete nasadit z většiny webových serverů, pokud jsou nakonfigurované odpovídající typy MIME (Multipurpose Internet Mail Extensions).</span><span class="sxs-lookup"><span data-stu-id="2376a-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="2376a-104">Ve výchozím nastavení [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] je nakonfigurovaná s těmito typy MIME, [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ale ne.</span><span class="sxs-lookup"><span data-stu-id="2376a-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these MIME types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>

<span data-ttu-id="2376a-105">Toto téma popisuje, jak nakonfigurovat [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nasadit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="2376a-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2376a-106">Můžete kontrolovat řetězec *userAgent* v registru, abyste zjistili, zda je systém .NET Framework nainstalován.</span><span class="sxs-lookup"><span data-stu-id="2376a-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="2376a-107">Podrobnosti a skript, který projde řetězec *userAgent* k určení, zda je v systému nainstalovaná .NET Framework, najdete v tématu [zjištění, zda je nainstalovaná .NET Framework 3,0](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2376a-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="2376a-108">Úprava nastavení vypršení platnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="2376a-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="2376a-109">Nastavení vypršení platnosti obsahu byste měli upravit na 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="2376a-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="2376a-110">Následující postup popisuje, jak to provést s nástrojem [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2376a-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>

1. <span data-ttu-id="2376a-111">Klikněte na nabídku **Start** , přejděte na **Nástroje pro správu**a klikněte na **Správce služby Internetová informační služba (IIS)** .</span><span class="sxs-lookup"><span data-stu-id="2376a-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="2376a-112">Tuto aplikaci můžete také spustit z příkazového řádku pomocí příkazu "%SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="2376a-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="2376a-113">Rozbalte stromovou strukturu, dokud nenajdete výchozí uzel webu. [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2376a-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="2376a-114">Klikněte pravým tlačítkem na **výchozí web** a v místní nabídce vyberte **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="2376a-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="2376a-115">Vyberte kartu **hlavičky protokolu HTTP** a klikněte na Povolit vypršení platnosti obsahu.</span><span class="sxs-lookup"><span data-stu-id="2376a-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="2376a-116">Nastavte, aby platnost obsahu vypršela po 1 minutách.</span><span class="sxs-lookup"><span data-stu-id="2376a-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="2376a-117">Registrace typů MIME a přípon souborů</span><span class="sxs-lookup"><span data-stu-id="2376a-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="2376a-118">Je nutné zaregistrovat několik typů MIME a přípon souborů, aby prohlížeč v systému klienta mohl načíst správnou obslužnou rutinu.</span><span class="sxs-lookup"><span data-stu-id="2376a-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="2376a-119">Je nutné přidat následující typy:</span><span class="sxs-lookup"><span data-stu-id="2376a-119">You need to add the following types:</span></span>

|<span data-ttu-id="2376a-120">Linka</span><span class="sxs-lookup"><span data-stu-id="2376a-120">Extension</span></span>|<span data-ttu-id="2376a-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="2376a-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="2376a-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="2376a-122">.manifest</span></span>|<span data-ttu-id="2376a-123">Aplikace/manifest</span><span class="sxs-lookup"><span data-stu-id="2376a-123">application/manifest</span></span>|
|<span data-ttu-id="2376a-124">. XAML</span><span class="sxs-lookup"><span data-stu-id="2376a-124">.xaml</span></span>|<span data-ttu-id="2376a-125">Application/XAML + XML</span><span class="sxs-lookup"><span data-stu-id="2376a-125">application/xaml+xml</span></span>|
|<span data-ttu-id="2376a-126">. Application</span><span class="sxs-lookup"><span data-stu-id="2376a-126">.application</span></span>|<span data-ttu-id="2376a-127">aplikace/x-MS-aplikace</span><span class="sxs-lookup"><span data-stu-id="2376a-127">application/x-ms-application</span></span>|
|<span data-ttu-id="2376a-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="2376a-128">.xbap</span></span>|<span data-ttu-id="2376a-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="2376a-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="2376a-130">. deploy</span><span class="sxs-lookup"><span data-stu-id="2376a-130">.deploy</span></span>|<span data-ttu-id="2376a-131">aplikace/oktet – Stream</span><span class="sxs-lookup"><span data-stu-id="2376a-131">application/octet-stream</span></span>|
|<span data-ttu-id="2376a-132">. XPS</span><span class="sxs-lookup"><span data-stu-id="2376a-132">.xps</span></span>|<span data-ttu-id="2376a-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="2376a-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="2376a-134">V klientských systémech nemusíte registrovat typy MIME ani přípony souborů.</span><span class="sxs-lookup"><span data-stu-id="2376a-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="2376a-135">Jsou zaregistrovány automaticky při instalaci aplikace Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2376a-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="2376a-136">Následující ukázka jazyka VBScript (Microsoft Visual Basic Scripting Edition) automaticky přidá nezbytné typy MIME do [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2376a-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="2376a-137">Chcete-li použít skript, zkopírujte kód do souboru. vbs na vašem serveru.</span><span class="sxs-lookup"><span data-stu-id="2376a-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="2376a-138">Potom spusťte skript spuštěním souboru z příkazového řádku nebo Poklikáním na soubor v [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2376a-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>

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
> <span data-ttu-id="2376a-139">Spuštění tohoto skriptu několikrát vytvoří v [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabázi nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] několik položek mapování MIME.</span><span class="sxs-lookup"><span data-stu-id="2376a-139">Running this script multiple times creates multiple MIME map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

<span data-ttu-id="2376a-140">Po spuštění tohoto skriptu nesmíte zobrazit další typy MIME z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] konzoly konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="2376a-140">After you have run this script, you may not see additional MIME types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Microsoft Management Console (MMC).</span></span> <span data-ttu-id="2376a-141">Tyto typy MIME se ale přidaly do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabáze nebo. [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2376a-141">However, these MIME types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="2376a-142">Následující skript zobrazí všechny typy MIME v [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabázi nebo. [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2376a-142">The following script will display all the MIME types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

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

<span data-ttu-id="2376a-143">Uložte skript jako `.vbs` soubor ( `DiscoverIISMimeTypes.vbs`například) a spusťte ho z příkazového řádku pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2376a-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
