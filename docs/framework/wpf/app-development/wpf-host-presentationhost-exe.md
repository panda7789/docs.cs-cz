---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: eda34c71f5735ae7ea3fcedea3a400e92756243b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972260"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="e41e2-102">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e41e2-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="e41e2-103">Hostitel Windows Presentation Foundation (WPF) (PresentationHost. exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hostování aplikací v kompatibilních prohlížečích (včetně aplikace Microsoft Internet Explorer 6 a novější).</span><span class="sxs-lookup"><span data-stu-id="e41e2-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="e41e2-104">Ve výchozím nastavení je hostitel Windows Presentation Foundation (WPF) zaregistrován jako prostředí a obslužná rutina MIME pro obsah hostovaný [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v prohlížeči, což zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="e41e2-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
- <span data-ttu-id="e41e2-105">Volné (nekompilované) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (. XAML).</span><span class="sxs-lookup"><span data-stu-id="e41e2-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="e41e2-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="e41e2-106">(.xbap).</span></span>  
  
 <span data-ttu-id="e41e2-107">Pro soubory těchto typů hostitel Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="e41e2-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="e41e2-108">Spustí zaregistrovanou obslužnou rutinu HTML pro hostování obsahu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e41e2-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="e41e2-109">Načte správné verze požadovaných sestavení modulu CLR (Common Language Runtime) a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e41e2-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="e41e2-110">Zajišťuje, aby byly správné úrovně oprávnění pro zónu nasazení.</span><span class="sxs-lookup"><span data-stu-id="e41e2-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="e41e2-111">Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="e41e2-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e41e2-112">Použití</span><span class="sxs-lookup"><span data-stu-id="e41e2-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="e41e2-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="e41e2-113">Parameters</span></span>  
  
|<span data-ttu-id="e41e2-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="e41e2-114">Parameter</span></span>|<span data-ttu-id="e41e2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e41e2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e41e2-116">filename</span><span class="sxs-lookup"><span data-stu-id="e41e2-116">filename</span></span>|<span data-ttu-id="e41e2-117">Cesta k souboru, který se má aktivovat</span><span class="sxs-lookup"><span data-stu-id="e41e2-117">The path of the file to be activated.</span></span> <span data-ttu-id="e41e2-118">Může to [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]být také.</span><span class="sxs-lookup"><span data-stu-id="e41e2-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="e41e2-119">-debug</span><span class="sxs-lookup"><span data-stu-id="e41e2-119">-debug</span></span>|<span data-ttu-id="e41e2-120">Při aktivaci aplikace ji nepotvrdí ani nespustí ze Storu.</span><span class="sxs-lookup"><span data-stu-id="e41e2-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="e41e2-121">Tato funkce funguje pouze v případě, že je aktivován místní soubor.</span><span class="sxs-lookup"><span data-stu-id="e41e2-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="e41e2-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="e41e2-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="e41e2-123">Používá se s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotou pro indikaci PresentationHost. exe, že by měla být aplikace Laděna, jako kdyby byla nasazena ze zadaného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e41e2-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="e41e2-124">Tím se určuje jak zóna nasazení, tak původní lokalita.</span><span class="sxs-lookup"><span data-stu-id="e41e2-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="e41e2-125">– vkládání</span><span class="sxs-lookup"><span data-stu-id="e41e2-125">-embedding</span></span>|<span data-ttu-id="e41e2-126">Požadováno OLE.</span><span class="sxs-lookup"><span data-stu-id="e41e2-126">Required by OLE.</span></span> <span data-ttu-id="e41e2-127">Je-li `-debug` zadán parametr `-embedding` `-event` nebo, není nutné parametr zadat, protože tento parametr je nastaven interně.</span><span class="sxs-lookup"><span data-stu-id="e41e2-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="e41e2-128">-> \<události EventName</span><span class="sxs-lookup"><span data-stu-id="e41e2-128">-event \<eventname></span></span>|<span data-ttu-id="e41e2-129">Otevřete událost s tímto názvem a nazvěte ji, když se PresentationHost. exe inicializuje a je připravený [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na hostování obsahu.</span><span class="sxs-lookup"><span data-stu-id="e41e2-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="e41e2-130">PresentationHost. exe skončí, pokud došlo k chybě při otevírání události, například pokud ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="e41e2-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="e41e2-131">– launchApplication \<URL ></span><span class="sxs-lookup"><span data-stu-id="e41e2-131">-launchApplication \<url></span></span>|<span data-ttu-id="e41e2-132">Spustí samostatnou aplikaci ClickOnce ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="e41e2-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="e41e2-133">Aplikují se zásady zabezpečení Internet Exploreru a WinINet týkající se aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="e41e2-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="e41e2-134">Scénáře</span><span class="sxs-lookup"><span data-stu-id="e41e2-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="e41e2-135">Obslužná rutina prostředí</span><span class="sxs-lookup"><span data-stu-id="e41e2-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="e41e2-136">Obslužná rutina MIME</span><span class="sxs-lookup"><span data-stu-id="e41e2-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="e41e2-137">Ladění sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e41e2-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="e41e2-138">Ladění sady Visual Studio v zóně</span><span class="sxs-lookup"><span data-stu-id="e41e2-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="e41e2-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e41e2-139">See also</span></span>

- [<span data-ttu-id="e41e2-140">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e41e2-140">Security</span></span>](../security-wpf.md)
