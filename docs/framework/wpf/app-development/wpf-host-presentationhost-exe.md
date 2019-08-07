---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 88e4c6895039c84a57ed215a37a10a4b68851b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817922"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="a6f5c-102">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a6f5c-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="a6f5c-103">Hostitel Windows Presentation Foundation (WPF) (PresentationHost. exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostování aplikací v kompatibilních prohlížečích (včetně aplikace Microsoft Internet Explorer 6 a novější).</span><span class="sxs-lookup"><span data-stu-id="a6f5c-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="a6f5c-104">Ve výchozím nastavení je hostitel Windows Presentation Foundation (WPF) zaregistrován jako prostředí a [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] obslužné rutiny obsahu hostovaného [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v prohlížeči, což zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="a6f5c-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="a6f5c-105">Volné (nekompilované) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (. XAML).</span><span class="sxs-lookup"><span data-stu-id="a6f5c-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="a6f5c-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="a6f5c-106">(.xbap).</span></span>  
  
 <span data-ttu-id="a6f5c-107">Pro soubory těchto typů hostitel Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="a6f5c-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="a6f5c-108">Spustí zaregistrovanou obslužnou rutinu HTML pro hostování obsahu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a6f5c-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="a6f5c-109">Načte správné verze požadovaných sestavení modulu CLR (Common Language Runtime) a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a6f5c-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="a6f5c-110">Zajišťuje, aby byly správné úrovně oprávnění pro zónu nasazení.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="a6f5c-111">Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="a6f5c-112">Použití</span><span class="sxs-lookup"><span data-stu-id="a6f5c-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="a6f5c-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6f5c-113">Parameters</span></span>  
  
|<span data-ttu-id="a6f5c-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="a6f5c-114">Parameter</span></span>|<span data-ttu-id="a6f5c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a6f5c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6f5c-116">filename</span><span class="sxs-lookup"><span data-stu-id="a6f5c-116">filename</span></span>|<span data-ttu-id="a6f5c-117">Cesta k souboru, který se má aktivovat</span><span class="sxs-lookup"><span data-stu-id="a6f5c-117">The path of the file to be activated.</span></span> <span data-ttu-id="a6f5c-118">Může to [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]být také.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="a6f5c-119">-debug</span><span class="sxs-lookup"><span data-stu-id="a6f5c-119">-debug</span></span>|<span data-ttu-id="a6f5c-120">Při aktivaci aplikace ji nepotvrdí ani nespustí ze Storu.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="a6f5c-121">Tato funkce funguje pouze v případě, že je aktivován místní soubor.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="a6f5c-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="a6f5c-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="a6f5c-123">Používá se s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotou pro indikaci PresentationHost. exe, že by měla být aplikace Laděna, jako kdyby byla nasazena ze zadaného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6f5c-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="a6f5c-124">Tím se určuje jak zóna nasazení, tak původní lokalita.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="a6f5c-125">– vkládání</span><span class="sxs-lookup"><span data-stu-id="a6f5c-125">-embedding</span></span>|<span data-ttu-id="a6f5c-126">Požadováno OLE.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-126">Required by OLE.</span></span> <span data-ttu-id="a6f5c-127">Je-li `-debug` zadán parametr `-embedding` `-event` nebo, není nutné parametr zadat, protože tento parametr je nastaven interně.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="a6f5c-128">-> \<události EventName</span><span class="sxs-lookup"><span data-stu-id="a6f5c-128">-event \<eventname></span></span>|<span data-ttu-id="a6f5c-129">Otevřete událost s tímto názvem a nazvěte ji, když se PresentationHost. exe inicializuje a je připravený [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na hostování obsahu.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="a6f5c-130">PresentationHost. exe skončí, pokud došlo k chybě při otevírání události, například pokud ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="a6f5c-131">– launchApplication \<URL ></span><span class="sxs-lookup"><span data-stu-id="a6f5c-131">-launchApplication \<url></span></span>|<span data-ttu-id="a6f5c-132">Spustí samostatnou aplikaci ClickOnce ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="a6f5c-133">Aplikují se zásady zabezpečení Internet Exploreru a WinINet týkající se aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="a6f5c-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="a6f5c-134">Scénáře</span><span class="sxs-lookup"><span data-stu-id="a6f5c-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="a6f5c-135">Obslužná rutina prostředí</span><span class="sxs-lookup"><span data-stu-id="a6f5c-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="a6f5c-136">Obslužná rutina MIME</span><span class="sxs-lookup"><span data-stu-id="a6f5c-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="a6f5c-137">Ladění sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a6f5c-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="a6f5c-138">Ladění sady Visual Studio v zóně</span><span class="sxs-lookup"><span data-stu-id="a6f5c-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="a6f5c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6f5c-139">See also</span></span>

- [<span data-ttu-id="a6f5c-140">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a6f5c-140">Security</span></span>](../security-wpf.md)
