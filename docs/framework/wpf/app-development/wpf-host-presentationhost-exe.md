---
title: Hostitel WPF (PresentationHost.exe)
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: bda7efbb1b7a4760199215bdb58c12b3063e290c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743396"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="c8fda-102">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="c8fda-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="c8fda-103">Hostitel Windows Presentation Foundation (WPF) (PresentationHost. exe) je aplikace, která umožňuje hostování aplikací WPF v kompatibilních prohlížečích (včetně aplikace Microsoft Internet Explorer 6 a novější).</span><span class="sxs-lookup"><span data-stu-id="c8fda-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="c8fda-104">Ve výchozím nastavení je hostitel Windows Presentation Foundation (WPF) zaregistrován jako prostředí a obslužná rutina MIME pro obsah WPF hostovaná v prohlížeči, což zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="c8fda-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="c8fda-105">Volné (nekompilované) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (. XAML).</span><span class="sxs-lookup"><span data-stu-id="c8fda-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="c8fda-106">Aplikace prohlížeče XAML (XBAP) (. XBAP)</span><span class="sxs-lookup"><span data-stu-id="c8fda-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="c8fda-107">Pro soubory těchto typů hostitel Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="c8fda-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="c8fda-108">Spustí zaregistrovanou obslužnou rutinu HTML pro hostování obsahu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c8fda-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="c8fda-109">Načte správné verze požadovaných sestavení modulu CLR (Common Language Runtime) a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="c8fda-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="c8fda-110">Zajišťuje, aby byly správné úrovně oprávnění pro zónu nasazení.</span><span class="sxs-lookup"><span data-stu-id="c8fda-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="c8fda-111">Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="c8fda-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c8fda-112">Využití</span><span class="sxs-lookup"><span data-stu-id="c8fda-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="c8fda-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8fda-113">Parameters</span></span>  
  
|<span data-ttu-id="c8fda-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="c8fda-114">Parameter</span></span>|<span data-ttu-id="c8fda-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c8fda-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8fda-116">filename</span><span class="sxs-lookup"><span data-stu-id="c8fda-116">filename</span></span>|<span data-ttu-id="c8fda-117">Cesta k souboru, který se má aktivovat</span><span class="sxs-lookup"><span data-stu-id="c8fda-117">The path of the file to be activated.</span></span> <span data-ttu-id="c8fda-118">Může to být také identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="c8fda-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="c8fda-119">-debug</span><span class="sxs-lookup"><span data-stu-id="c8fda-119">-debug</span></span>|<span data-ttu-id="c8fda-120">Při aktivaci aplikace ji nepotvrdí ani nespustí ze Storu.</span><span class="sxs-lookup"><span data-stu-id="c8fda-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="c8fda-121">Tato funkce funguje pouze v případě, že je aktivován místní soubor.</span><span class="sxs-lookup"><span data-stu-id="c8fda-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="c8fda-122">– debugSecurityZoneURL \<adresa URL ></span><span class="sxs-lookup"><span data-stu-id="c8fda-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="c8fda-123">Používá se s hodnotou adresy URL k označení PresentationHost. exe, že by měla být aplikace Laděna, jako kdyby byla nasazena ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="c8fda-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="c8fda-124">Tím se určuje jak zóna nasazení, tak původní lokalita.</span><span class="sxs-lookup"><span data-stu-id="c8fda-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="c8fda-125">– vkládání</span><span class="sxs-lookup"><span data-stu-id="c8fda-125">-embedding</span></span>|<span data-ttu-id="c8fda-126">Požadováno OLE.</span><span class="sxs-lookup"><span data-stu-id="c8fda-126">Required by OLE.</span></span> <span data-ttu-id="c8fda-127">Je-li zadán parametr `-event` nebo `-debug`, není nutné zadávat parametr `-embedding`, protože tento parametr je nastaven interně.</span><span class="sxs-lookup"><span data-stu-id="c8fda-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="c8fda-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="c8fda-128">-event \<eventname></span></span>|<span data-ttu-id="c8fda-129">Otevřete událost s tímto názvem a nazvěte ji, když se PresentationHost. exe inicializuje a je připravený na hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="c8fda-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="c8fda-130">PresentationHost. exe skončí, pokud došlo k chybě při otevírání události, například pokud ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="c8fda-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="c8fda-131">– launchApplication \<adresa URL ></span><span class="sxs-lookup"><span data-stu-id="c8fda-131">-launchApplication \<url></span></span>|<span data-ttu-id="c8fda-132">Spustí samostatnou aplikaci ClickOnce ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="c8fda-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="c8fda-133">Aplikují se zásady zabezpečení Internet Exploreru a WinINet týkající se aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="c8fda-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="c8fda-134">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c8fda-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="c8fda-135">Obslužná rutina prostředí</span><span class="sxs-lookup"><span data-stu-id="c8fda-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="c8fda-136">Obslužná rutina MIME</span><span class="sxs-lookup"><span data-stu-id="c8fda-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="c8fda-137">Ladění sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c8fda-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="c8fda-138">Ladění sady Visual Studio v zóně</span><span class="sxs-lookup"><span data-stu-id="c8fda-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="c8fda-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8fda-139">See also</span></span>

- [<span data-ttu-id="c8fda-140">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c8fda-140">Security</span></span>](../security-wpf.md)
