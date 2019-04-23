---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 586d306d0f375241c9382e1e24cf1af75b990ba9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122860"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="b72b7-102">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="b72b7-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="b72b7-103">Hostitel Windows Presentation Foundation (WPF) (PresentationHost.exe) je aplikace, která umožňuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace zajistit také jejich hostování v kompatibilní prohlížečů (včetně [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] a novější).</span><span class="sxs-lookup"><span data-stu-id="b72b7-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="b72b7-104">Ve výchozím nastavení, je Windows Presentation Foundation (WPF) hostitele zaregistrovaný jako prostředí a [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] obslužné rutiny pro hostované v prohlížeči [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah, který obsahuje:</span><span class="sxs-lookup"><span data-stu-id="b72b7-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="b72b7-105">Přijít o provedené (– nezkompilovaný) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (.xaml).</span><span class="sxs-lookup"><span data-stu-id="b72b7-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] <span data-ttu-id="b72b7-106">(.xbap).</span><span class="sxs-lookup"><span data-stu-id="b72b7-106">(.xbap).</span></span>  
  
 <span data-ttu-id="b72b7-107">Pro soubory z těchto typů hostitele Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="b72b7-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
-   <span data-ttu-id="b72b7-108">Spustí zaregistrovanou [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] obslužné rutiny pro hostování daného obsahu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b72b7-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
-   <span data-ttu-id="b72b7-109">Načte správné verze požadované [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] a sestavení Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="b72b7-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
-   <span data-ttu-id="b72b7-110">Zajišťuje, že příslušná úroveň oprávnění pro zónu nasazení jsou na místě.</span><span class="sxs-lookup"><span data-stu-id="b72b7-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="b72b7-111">Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="b72b7-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b72b7-112">Použití</span><span class="sxs-lookup"><span data-stu-id="b72b7-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="b72b7-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="b72b7-113">Parameters</span></span>  
  
|<span data-ttu-id="b72b7-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="b72b7-114">Parameter</span></span>|<span data-ttu-id="b72b7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b72b7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b72b7-116">filename</span><span class="sxs-lookup"><span data-stu-id="b72b7-116">filename</span></span>|<span data-ttu-id="b72b7-117">Cesta souboru, který má být aktivován.</span><span class="sxs-lookup"><span data-stu-id="b72b7-117">The path of the file to be activated.</span></span> <span data-ttu-id="b72b7-118">Může být také [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b72b7-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="b72b7-119">-debug</span><span class="sxs-lookup"><span data-stu-id="b72b7-119">-debug</span></span>|<span data-ttu-id="b72b7-120">Při aktivaci aplikace, není na potvrzení nebo spuštění z úložiště.</span><span class="sxs-lookup"><span data-stu-id="b72b7-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="b72b7-121">Toto funguje pouze v případě místního souboru se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="b72b7-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="b72b7-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="b72b7-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="b72b7-123">Použít s [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] hodnotě k označení PresentationHost.exe, aplikace by měl ladit, jako kdyby byly nasazeny z určeného [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b72b7-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="b72b7-124">Určuje zónu nasazení i webovou stránku původu.</span><span class="sxs-lookup"><span data-stu-id="b72b7-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="b72b7-125">-vkládání</span><span class="sxs-lookup"><span data-stu-id="b72b7-125">-embedding</span></span>|<span data-ttu-id="b72b7-126">Vyžadovány rozhraním OLE.</span><span class="sxs-lookup"><span data-stu-id="b72b7-126">Required by OLE.</span></span> <span data-ttu-id="b72b7-127">Pokud `-event` nebo `-debug` jsou parametr zadán, není potřeba zadávat `-embedding` parametr, protože tento parametr je nastaven interně.</span><span class="sxs-lookup"><span data-stu-id="b72b7-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="b72b7-128">-události \<eventname ></span><span class="sxs-lookup"><span data-stu-id="b72b7-128">-event \<eventname></span></span>|<span data-ttu-id="b72b7-129">Otevřete událost s tímto názvem a dají signál, jakmile je inicializována a jste připravení hostitele PresentationHost.exe [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="b72b7-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="b72b7-130">PresentationHost.exe bude ukončen. Pokud došlo k chybě při otevírání události, například když ji dosud nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="b72b7-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="b72b7-131">-launchApplication \<url ></span><span class="sxs-lookup"><span data-stu-id="b72b7-131">-launchApplication \<url></span></span>|<span data-ttu-id="b72b7-132">Spouští samostatný [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] ze zadané adresy URL aplikace.</span><span class="sxs-lookup"><span data-stu-id="b72b7-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] <span data-ttu-id="b72b7-133">a jsou použity zásady zabezpečení rozhraní WinINet týkající se aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="b72b7-133">and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="b72b7-134">Scénáře</span><span class="sxs-lookup"><span data-stu-id="b72b7-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="b72b7-135">Obslužná rutina prostředí</span><span class="sxs-lookup"><span data-stu-id="b72b7-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="b72b7-136">Obslužná rutina MIME</span><span class="sxs-lookup"><span data-stu-id="b72b7-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="b72b7-137">Ladění sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b72b7-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="b72b7-138">Ladění v zóně sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b72b7-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="b72b7-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b72b7-139">See also</span></span>

- [<span data-ttu-id="b72b7-140">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b72b7-140">Security</span></span>](../security-wpf.md)
