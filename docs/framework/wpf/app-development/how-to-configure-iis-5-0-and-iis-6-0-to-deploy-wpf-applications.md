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
ms.openlocfilehash: 6fa00c4ced8c05d056703560e5740689c6dcfe39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973665"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="507f5-102">Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="507f5-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="507f5-103">Můžete nasadit [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace z většiny webových serverů, jako jsou nakonfigurované s příslušnou [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typy.</span><span class="sxs-lookup"><span data-stu-id="507f5-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="507f5-104">Ve výchozím nastavení [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] je nakonfigurovaný s těmito [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nejsou.</span><span class="sxs-lookup"><span data-stu-id="507f5-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>

<span data-ttu-id="507f5-105">Toto téma popisuje postup konfigurace [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nasazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="507f5-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="507f5-106">Můžete zkontrolovat *UserAgent* řetězec v registru, který slouží k určení, zda má systém nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="507f5-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="507f5-107">Podrobnosti a skript, který ověřuje, zda *UserAgent* řetězce k určení, zda je v systému nainstalované rozhraní .NET Framework naleznete v tématu [zjistit, zda rozhraní .NET Framework 3.0 je nainstalována](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="507f5-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="507f5-108">Nastavení vypršení platnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="507f5-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="507f5-109">Je třeba upravit nastavení vypršení platnosti obsahu na 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="507f5-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="507f5-110">Následující postup ukazuje, jak to provést pomocí [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="507f5-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>

1. <span data-ttu-id="507f5-111">Klikněte na tlačítko **Start** nabídky, přejděte k **nástroje pro správu**a klikněte na tlačítko **Správce Internetové informační služby (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="507f5-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="507f5-112">Můžete také spustit tuto aplikaci z příkazového řádku: "% SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="507f5-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="507f5-113">Rozbalte [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] stromové struktury, dokud nenajdete **výchozí_webový_server** uzlu.</span><span class="sxs-lookup"><span data-stu-id="507f5-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="507f5-114">Klikněte pravým tlačítkem na **výchozí webová stránka** a vyberte **vlastnosti** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="507f5-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="507f5-115">Vyberte **hlavičky protokolu HTTP** kartě a klikněte na možnost "Povolit vypršení platnosti obsahu".</span><span class="sxs-lookup"><span data-stu-id="507f5-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="507f5-116">Nastavení obsahu vyprší za 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="507f5-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="507f5-117">Registrace typů MIME a přípony souborů</span><span class="sxs-lookup"><span data-stu-id="507f5-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="507f5-118">Je nutné zaregistrovat několik [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy a přípony souborů, které tak, aby prohlížeč v systému klienta můžete načíst obslužnou rutinu správné.</span><span class="sxs-lookup"><span data-stu-id="507f5-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="507f5-119">Je potřeba přidat následující typy:</span><span class="sxs-lookup"><span data-stu-id="507f5-119">You need to add the following types:</span></span>

|<span data-ttu-id="507f5-120">Linka</span><span class="sxs-lookup"><span data-stu-id="507f5-120">Extension</span></span>|<span data-ttu-id="507f5-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="507f5-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="507f5-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="507f5-122">.manifest</span></span>|<span data-ttu-id="507f5-123">/ manifest aplikace</span><span class="sxs-lookup"><span data-stu-id="507f5-123">application/manifest</span></span>|
|<span data-ttu-id="507f5-124">XAML</span><span class="sxs-lookup"><span data-stu-id="507f5-124">.xaml</span></span>|<span data-ttu-id="507f5-125">aplikace/xaml + xml</span><span class="sxs-lookup"><span data-stu-id="507f5-125">application/xaml+xml</span></span>|
|<span data-ttu-id="507f5-126">.Application</span><span class="sxs-lookup"><span data-stu-id="507f5-126">.application</span></span>|<span data-ttu-id="507f5-127">application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="507f5-127">application/x-ms-application</span></span>|
|<span data-ttu-id="507f5-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="507f5-128">.xbap</span></span>|<span data-ttu-id="507f5-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="507f5-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="507f5-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="507f5-130">.deploy</span></span>|<span data-ttu-id="507f5-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="507f5-131">application/octet-stream</span></span>|
|<span data-ttu-id="507f5-132">.xps</span><span class="sxs-lookup"><span data-stu-id="507f5-132">.xps</span></span>|<span data-ttu-id="507f5-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="507f5-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="507f5-134">Není potřeba registrovat [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy nebo přípony souborů na klientské systémy.</span><span class="sxs-lookup"><span data-stu-id="507f5-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="507f5-135">Jsou registrované automaticky při instalaci rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="507f5-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="507f5-136">Následující ukázka Microsoft Visual Basic Scripting Edition (VBScript) automaticky přidá nezbytná [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy mají [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="507f5-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="507f5-137">Použít skript, zkopírujte kód do souboru vbs na vašem serveru.</span><span class="sxs-lookup"><span data-stu-id="507f5-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="507f5-138">Potom spusťte skript spuštěním souboru z příkazového řádku nebo poklepáním na soubor v [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="507f5-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>

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
> <span data-ttu-id="507f5-139">Opakované spouštění tento skript vytvoří více [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] položky v mapování [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="507f5-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

<span data-ttu-id="507f5-140">Po spuštění tohoto skriptu nemusí zobrazit další [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="507f5-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="507f5-141">Ale tyto [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy jsou přidané do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="507f5-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="507f5-142">Následující skript se zobrazí všechny [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] napíše [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="507f5-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

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

<span data-ttu-id="507f5-143">Uložte skript pod názvem `.vbs` souboru (například `DiscoverIISMimeTypes.vbs`) a spouštět z příkazového řádku pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="507f5-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
