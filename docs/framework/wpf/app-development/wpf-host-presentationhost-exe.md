---
title: Hostitel WPF (PresentationHost.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
ms.openlocfilehash: 64ba1261134184f22e9faf157ca70e3471e3b3cb
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636247"
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="451b4-102">Hostitel WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="451b4-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="451b4-103">Hostitel Windows Presentation Foundation (WPF) (PresentationHost. exe) je aplikace, která umožňuje hostování aplikací WPF v kompatibilních prohlížečích (včetně aplikace Microsoft Internet Explorer 6 a novější).</span><span class="sxs-lookup"><span data-stu-id="451b4-103">Windows Presentation Foundation (WPF) Host (PresentationHost.exe) is the application that enables WPF applications to be hosted in compatible browsers (including Microsoft Internet Explorer 6 and later).</span></span> <span data-ttu-id="451b4-104">Ve výchozím nastavení je hostitel Windows Presentation Foundation (WPF) zaregistrován jako prostředí a obslužná rutina MIME pro obsah WPF hostovaná v prohlížeči, což zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="451b4-104">By default, Windows Presentation Foundation (WPF) Host is registered as the shell and MIME handler for browser-hosted WPF content, which includes:</span></span>  
  
- <span data-ttu-id="451b4-105">Volné (nekompilované) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory (. XAML).</span><span class="sxs-lookup"><span data-stu-id="451b4-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
- <span data-ttu-id="451b4-106">Aplikace prohlížeče XAML (XBAP) (. XBAP)</span><span class="sxs-lookup"><span data-stu-id="451b4-106">XAML browser application (XBAP) (.xbap).</span></span>  
  
 <span data-ttu-id="451b4-107">Pro soubory těchto typů hostitel Windows Presentation Foundation (WPF):</span><span class="sxs-lookup"><span data-stu-id="451b4-107">For files of these types, Windows Presentation Foundation (WPF) Host:</span></span>  
  
- <span data-ttu-id="451b4-108">Spustí zaregistrovanou obslužnou rutinu HTML pro hostování obsahu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="451b4-108">Launches the registered HTML handler to host the Windows Presentation Foundation (WPF) content.</span></span>  
  
- <span data-ttu-id="451b4-109">Načte správné verze požadovaných sestavení modulu CLR (Common Language Runtime) a Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="451b4-109">Loads the right versions of the required common language runtime (CLR) and Windows Presentation Foundation (WPF) assemblies.</span></span>  
  
- <span data-ttu-id="451b4-110">Zajišťuje, aby byly správné úrovně oprávnění pro zónu nasazení.</span><span class="sxs-lookup"><span data-stu-id="451b4-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="451b4-111">Toto téma popisuje parametry příkazového řádku, které lze použít s PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="451b4-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="451b4-112">Použití</span><span class="sxs-lookup"><span data-stu-id="451b4-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="451b4-113">Parametry</span><span class="sxs-lookup"><span data-stu-id="451b4-113">Parameters</span></span>  
  
|<span data-ttu-id="451b4-114">Parametr</span><span class="sxs-lookup"><span data-stu-id="451b4-114">Parameter</span></span>|<span data-ttu-id="451b4-115">Popis</span><span class="sxs-lookup"><span data-stu-id="451b4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="451b4-116">filename</span><span class="sxs-lookup"><span data-stu-id="451b4-116">filename</span></span>|<span data-ttu-id="451b4-117">Cesta k souboru, který se má aktivovat</span><span class="sxs-lookup"><span data-stu-id="451b4-117">The path of the file to be activated.</span></span> <span data-ttu-id="451b4-118">Může to být také identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="451b4-118">Can also be a URI.</span></span>|  
|<span data-ttu-id="451b4-119">-debug</span><span class="sxs-lookup"><span data-stu-id="451b4-119">-debug</span></span>|<span data-ttu-id="451b4-120">Při aktivaci aplikace ji nepotvrdí ani nespustí ze Storu.</span><span class="sxs-lookup"><span data-stu-id="451b4-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="451b4-121">Tato funkce funguje pouze v případě, že je aktivován místní soubor.</span><span class="sxs-lookup"><span data-stu-id="451b4-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="451b4-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="451b4-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="451b4-123">Používá se s hodnotou adresy URL k označení PresentationHost. exe, že by měla být aplikace Laděna, jako kdyby byla nasazena ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="451b4-123">Used with a URL value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified URL.</span></span> <span data-ttu-id="451b4-124">Tím se určuje jak zóna nasazení, tak původní lokalita.</span><span class="sxs-lookup"><span data-stu-id="451b4-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="451b4-125">– vkládání</span><span class="sxs-lookup"><span data-stu-id="451b4-125">-embedding</span></span>|<span data-ttu-id="451b4-126">Požadováno OLE.</span><span class="sxs-lookup"><span data-stu-id="451b4-126">Required by OLE.</span></span> <span data-ttu-id="451b4-127">Je-li zadán parametr `-event` nebo `-debug`, není nutné zadávat parametr `-embedding`, protože tento parametr je nastaven interně.</span><span class="sxs-lookup"><span data-stu-id="451b4-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="451b4-128">-Event \<EventName ></span><span class="sxs-lookup"><span data-stu-id="451b4-128">-event \<eventname></span></span>|<span data-ttu-id="451b4-129">Otevřete událost s tímto názvem a nazvěte ji, když se PresentationHost. exe inicializuje a je připravený na hostování obsahu WPF.</span><span class="sxs-lookup"><span data-stu-id="451b4-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host WPF content.</span></span> <span data-ttu-id="451b4-130">PresentationHost. exe skončí, pokud došlo k chybě při otevírání události, například pokud ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="451b4-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="451b4-131">– launchApplication \<adresa URL ></span><span class="sxs-lookup"><span data-stu-id="451b4-131">-launchApplication \<url></span></span>|<span data-ttu-id="451b4-132">Spustí samostatnou aplikaci ClickOnce ze zadané adresy URL.</span><span class="sxs-lookup"><span data-stu-id="451b4-132">Launches a standalone ClickOnce application from the specified URL.</span></span> <span data-ttu-id="451b4-133">Aplikují se zásady zabezpečení Internet Exploreru a WinINet týkající se aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="451b4-133">Internet Explorer and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="451b4-134">Scénáře</span><span class="sxs-lookup"><span data-stu-id="451b4-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="451b4-135">Obslužná rutina prostředí</span><span class="sxs-lookup"><span data-stu-id="451b4-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="451b4-136">Obslužná rutina MIME</span><span class="sxs-lookup"><span data-stu-id="451b4-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="451b4-137">Ladění sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="451b4-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="451b4-138">Ladění sady Visual Studio v zóně</span><span class="sxs-lookup"><span data-stu-id="451b4-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="451b4-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="451b4-139">See also</span></span>

- [<span data-ttu-id="451b4-140">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="451b4-140">Security</span></span>](../security-wpf.md)
