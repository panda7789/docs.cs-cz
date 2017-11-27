---
title: "Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: faff58f146aed7b309674157a5990cbce43dfb1f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="2e8c0-102">Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="2e8c0-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>
<span data-ttu-id="2e8c0-103">Můžete nasadit [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace z většina webové servery jsou nakonfigurovány s příslušnou [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typy.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="2e8c0-104">Ve výchozím nastavení [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] je nakonfigurována pomocí těchto [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nejsou.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>  
  
 <span data-ttu-id="2e8c0-105">Toto téma popisuje postup konfigurace [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nasazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>  
  
  
> [!NOTE]
>  <span data-ttu-id="2e8c0-106">Můžete zkontrolovat *UserAgent* řetězec v registru na určit, zda má systém [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] nainstalována.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-106">You can check the *UserAgent* string in the registry to determine whether a system has [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] installed.</span></span> <span data-ttu-id="2e8c0-107">Podrobnosti a skript, který ověřuje, zda *UserAgent* řetězec k určení zda [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] je nainstalován na systém, najdete v části [zjistit, zda rozhraní .NET Framework 3.0 je nainstalována](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="2e8c0-107">For details and a script that examines the *UserAgent* string to determine whether [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="2e8c0-108">Upravit nastavení doby platnosti obsahu</span><span class="sxs-lookup"><span data-stu-id="2e8c0-108">Adjust the Content Expiration Setting</span></span>  
 <span data-ttu-id="2e8c0-109">Má upravit nastavení doby platnosti obsahu na 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="2e8c0-110">Následující postup popisuje, jak to provést pomocí [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e8c0-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>  
  
1.  <span data-ttu-id="2e8c0-111">Klikněte na tlačítko **spustit** nabídky, přejděte na příkaz **nástroje pro správu**a klikněte na tlačítko **Správce Internetové informační služby (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="2e8c0-112">Můžete také spustit tuto aplikaci z příkazového řádku s "% SystemRoot%\system32\inetsrv\iis.msc".</span><span class="sxs-lookup"><span data-stu-id="2e8c0-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>  
  
2.  <span data-ttu-id="2e8c0-113">Rozbalte [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] stromu až naleznete **výchozí web** uzlu.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>  
  
3.  <span data-ttu-id="2e8c0-114">Klikněte pravým tlačítkem na **výchozí web** a vyberte **vlastnosti** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>  
  
4.  <span data-ttu-id="2e8c0-115">Vyberte **hlavičky protokolu HTTP** kartě a klikněte na možnost "Povolit vypršení platnosti obsahu".</span><span class="sxs-lookup"><span data-stu-id="2e8c0-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>  
  
5.  <span data-ttu-id="2e8c0-116">Nastavte obsah vyprší za 1 minutu.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-116">Set the content to expire after 1 minute.</span></span>  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="2e8c0-117">Typy MIME registrace a přípony souborů</span><span class="sxs-lookup"><span data-stu-id="2e8c0-117">Register MIME Types and File Extensions</span></span>  
 <span data-ttu-id="2e8c0-118">Je nutné zaregistrovat několik [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy a přípony souborů, aby prohlížeč v systému klienta můžete načíst obslužnou rutinu správné.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="2e8c0-119">Je nutné přidat následující typy:</span><span class="sxs-lookup"><span data-stu-id="2e8c0-119">You need to add the following types:</span></span>  
  
|<span data-ttu-id="2e8c0-120">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="2e8c0-120">Extension</span></span>|<span data-ttu-id="2e8c0-121">Typ MIME</span><span class="sxs-lookup"><span data-stu-id="2e8c0-121">MIME Type</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="2e8c0-122">manifest</span><span class="sxs-lookup"><span data-stu-id="2e8c0-122">.manifest</span></span>|<span data-ttu-id="2e8c0-123">/ manifest aplikace</span><span class="sxs-lookup"><span data-stu-id="2e8c0-123">application/manifest</span></span>|  
|<span data-ttu-id="2e8c0-124">XAML</span><span class="sxs-lookup"><span data-stu-id="2e8c0-124">.xaml</span></span>|<span data-ttu-id="2e8c0-125">aplikace nebo xaml + xml</span><span class="sxs-lookup"><span data-stu-id="2e8c0-125">application/xaml+xml</span></span>|  
|<span data-ttu-id="2e8c0-126">.Application</span><span class="sxs-lookup"><span data-stu-id="2e8c0-126">.application</span></span>|<span data-ttu-id="2e8c0-127">Application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="2e8c0-127">application/x-ms-application</span></span>|  
|<span data-ttu-id="2e8c0-128">.XBAP</span><span class="sxs-lookup"><span data-stu-id="2e8c0-128">.xbap</span></span>|<span data-ttu-id="2e8c0-129">Application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="2e8c0-129">application/x-ms-xbap</span></span>|  
|<span data-ttu-id="2e8c0-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="2e8c0-130">.deploy</span></span>|<span data-ttu-id="2e8c0-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="2e8c0-131">application/octet-stream</span></span>|  
|<span data-ttu-id="2e8c0-132">XPS</span><span class="sxs-lookup"><span data-stu-id="2e8c0-132">.xps</span></span>|<span data-ttu-id="2e8c0-133">aplikace nebo vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="2e8c0-133">application/vnd.ms-xpsdocument</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2e8c0-134">Není potřeba zaregistrovat [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy a přípony souborů v systémech klientů.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="2e8c0-135">Jsou při instalaci automaticky registrované [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e8c0-135">They are registered automatically when you install [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)].</span></span>  
  
 <span data-ttu-id="2e8c0-136">Následující [!INCLUDE[TLA#tla_visualbscrpt](../../../../includes/tlasharptla-visualbscrpt-md.md)] ukázka automaticky přidá nezbytné [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typů, který [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e8c0-136">The following [!INCLUDE[TLA#tla_visualbscrpt](../../../../includes/tlasharptla-visualbscrpt-md.md)] sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="2e8c0-137">Chcete-li použít skript, zkopírujte kód do souboru .vbs na vašem serveru.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="2e8c0-138">Spusťte skript spuštěný soubor z příkazového řádku nebo dvojitým kliknutím na soubor v [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e8c0-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>  
  
```  
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
  
' Get the mimemap object   
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
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="2e8c0-139">Spuštěním tohoto skriptu vícekrát vytváří více [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] mapování položek v [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
 <span data-ttu-id="2e8c0-140">Po spuštění tohoto skriptu nemusíte vidět další [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e8c0-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="2e8c0-141">Ale tyto [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy jsou přidané do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="2e8c0-142">Následující skript se zobrazí všechny [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy, které do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.</span><span class="sxs-lookup"><span data-stu-id="2e8c0-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 <span data-ttu-id="2e8c0-143">Uložte skript pod názvem `.vbs` souboru (například `DiscoverIISMimeTypes.vbs`) a potom ho spusťte z příkazového řádku pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="2e8c0-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>  
  
 `cscript DiscoverIISMimeTypes.vbs`
