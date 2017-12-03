---
title: "Nástroj WorkFlow Service Registration (WFServicesReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6a009193a88c588a19c324353296a78e27617df
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="06b55-102">Nástroj WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="06b55-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="06b55-103">Nástroj pro registraci služby pracovního postupu (WFServicesReg.exe) je samostatný nástroj, který slouží k přidání, odebrání nebo opravte konfigurační prvky pro služby systému Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="06b55-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06b55-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="06b55-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06b55-105">Remarks</span></span>  
 <span data-ttu-id="06b55-106">Tento nástroj najdete na [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] umístění instalace, konkrétně % windir%\Microsoft.NET\Framework\v3.5, nebo v %windir%\Microsoft.NET\Framework64\v3.5 v 64bitové počítače.</span><span class="sxs-lookup"><span data-stu-id="06b55-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="06b55-107">Následující tabulka popisuje možnosti, které lze použít s nástroj pro registraci služby pracovního postupu (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="06b55-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="06b55-108">Možnost</span><span class="sxs-lookup"><span data-stu-id="06b55-108">Option</span></span>|<span data-ttu-id="06b55-109">Popis</span><span class="sxs-lookup"><span data-stu-id="06b55-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="06b55-110">Nakonfiguruje službu pracovního postupu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="06b55-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="06b55-111">Použít v instalaci a opravte scénáře.</span><span class="sxs-lookup"><span data-stu-id="06b55-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="06b55-112">Odebere konfigurace služby pracovního postupu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="06b55-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="06b55-113">Tisk podrobné informace (pro konfiguraci nebo odebrání).</span><span class="sxs-lookup"><span data-stu-id="06b55-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="06b55-114">Umožňuje formát protokolování MSI.</span><span class="sxs-lookup"><span data-stu-id="06b55-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="06b55-115">Minimalizuje okno, pokud je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="06b55-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="06b55-116">Registrace</span><span class="sxs-lookup"><span data-stu-id="06b55-116">Registration</span></span>  
 <span data-ttu-id="06b55-117">Tento nástroj kontroluje v souboru Web.config a zaregistruje následující:</span><span class="sxs-lookup"><span data-stu-id="06b55-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<span data-ttu-id="06b55-118">referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="06b55-118"> reference assemblies.</span></span>  
  
-   <span data-ttu-id="06b55-119">Sestavení zprostředkovatele pro soubory XOML.</span><span class="sxs-lookup"><span data-stu-id="06b55-119">A build provider for .xoml files.</span></span>  
  
-   <span data-ttu-id="06b55-120">Obslužné rutiny HTTP XOML a .rules souborů.</span><span class="sxs-lookup"><span data-stu-id="06b55-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="06b55-121">Tento nástroj kontroluje souboru Machine.config a zaregistruje následující rozšíření:</span><span class="sxs-lookup"><span data-stu-id="06b55-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
-   <span data-ttu-id="06b55-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="06b55-122">behaviorExtensions</span></span>  
  
-   <span data-ttu-id="06b55-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="06b55-123">bindingElementExtensions</span></span>  
  
-   <span data-ttu-id="06b55-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="06b55-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="06b55-125">Nástroj také zaregistruje následující společnosti metadata importers pro klienta:</span><span class="sxs-lookup"><span data-stu-id="06b55-125">The tool also registers the following client metadata importers:</span></span>  
  
-   <span data-ttu-id="06b55-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="06b55-126">policyImporters</span></span>  
  
-   <span data-ttu-id="06b55-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="06b55-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="06b55-128">Nástroj také zaregistruje XOML a .rules mapy skriptů a obslužné rutiny v metabázi služby IIS.</span><span class="sxs-lookup"><span data-stu-id="06b55-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="06b55-129">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)] počítače (služba IIS 5.1 a [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jedna sada XOML a .rules mapy skriptů jsou registrované.</span><span class="sxs-lookup"><span data-stu-id="06b55-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="06b55-130">Na 64bitových počítačích, nástroj zaregistruje mapy skriptů režimu WOW, pokud `Enable32BitAppOnWin64` přepínač je povolený nebo nativní 64bitové verze mapy skriptů, pokud `Enable32BitAppOnWin64` přepínač je zakázána.</span><span class="sxs-lookup"><span data-stu-id="06b55-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="06b55-131">Na [!INCLUDE[wv](../../../includes/wv-md.md)] a Windows Server 2008 (služby IIS 7.0 a vyšší) jsou registrované počítače, dvě sady XOML a .rules obslužné rutiny: jeden pro integrovaný režim a jeden pro klasický režim.</span><span class="sxs-lookup"><span data-stu-id="06b55-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="06b55-132">Na 64bitové počítače jsou registrované tři sady obslužné rutiny (bez ohledu na stav `Enable32BitAppOnWin64` přepínače): jeden pro integrovaný režim, jednu pro WOW klasickém režimu a jeden pro nativní 64bitové verze klasickém režimu.</span><span class="sxs-lookup"><span data-stu-id="06b55-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06b55-133">Na rozdíl od ServiceModelreg.exe WFServicesReg.exe nepovoluje přidání, odebrání nebo opravu mapy skriptů nebo obslužné rutiny pro konkrétní web.</span><span class="sxs-lookup"><span data-stu-id="06b55-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="06b55-134">Alternativní řešení tohoto problému najdete v části "Oprava mapy skriptů".</span><span class="sxs-lookup"><span data-stu-id="06b55-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="06b55-135">Scénáře použití</span><span class="sxs-lookup"><span data-stu-id="06b55-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="06b55-136">Instalace služby IIS po instalaci rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="06b55-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="06b55-137">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítače [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalována před instalací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="06b55-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="06b55-138">Z důvodu nedostupnosti metabáze služby IIS, instalace [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] úspěšné bez instalace XOML a .rules mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="06b55-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="06b55-139">Po instalaci služby IIS, můžete použít nástroj WFServicesReg.exe s `/c` přepínač tak, aby nainstalovat tyto konkrétní mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="06b55-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="06b55-140">Oprava mapy skriptů</span><span class="sxs-lookup"><span data-stu-id="06b55-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="06b55-141">Mapování skriptů odstranit pod uzlem webové stránky</span><span class="sxs-lookup"><span data-stu-id="06b55-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="06b55-142">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules se náhodou smazala z uzlu webových serverů.</span><span class="sxs-lookup"><span data-stu-id="06b55-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="06b55-143">To lze opravit spuštěním nástroje WFServicesReg.exe s `/c` přepínače.</span><span class="sxs-lookup"><span data-stu-id="06b55-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="06b55-144">Mapování skriptů odstranit v rámci určitého webového serveru</span><span class="sxs-lookup"><span data-stu-id="06b55-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="06b55-145">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač XOML odstraněna nebo .rules je náhodně z určitého webového serveru (například výchozí web) a nikoli z uzlu webových serverů.</span><span class="sxs-lookup"><span data-stu-id="06b55-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="06b55-146">K opravě odstraněné obslužné rutiny pro určitý web, byste měli spustit "WFServicesReg.exe r" odebrat obslužné rutiny ze všech webů, spusťte "WFServicesReg.exe c" k vytvoření odpovídající obslužné rutiny pro všechny weby.</span><span class="sxs-lookup"><span data-stu-id="06b55-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="06b55-147">Konfigurace obslužné rutiny po přepnutí režimu služby IIS</span><span class="sxs-lookup"><span data-stu-id="06b55-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="06b55-148">Pokud služby IIS je v režimu sdílené konfigurace a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalovaná, metabáze služby IIS je nakonfigurovaný pod sdílené umístění.</span><span class="sxs-lookup"><span data-stu-id="06b55-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="06b55-149">Pokud přejdete na režim nesdílené konfigurace služby IIS, nebude obsahovat místní metabáze požadované obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="06b55-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="06b55-150">Konfigurace místního metabáze správně, můžete buď importovat sdílené metabáze na místní nebo spuštění "WFServicesReg.exe /c", který nakonfiguruje místní metabáze.</span><span class="sxs-lookup"><span data-stu-id="06b55-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
