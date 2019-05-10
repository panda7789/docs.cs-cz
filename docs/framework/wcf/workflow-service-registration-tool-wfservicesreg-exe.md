---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: da377e865258169bdca16cfb0db3f8612d4e0f0d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613067"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="5b1df-102">Nástroj WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="5b1df-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="5b1df-103">Nástroj pro registraci služby pracovních postupů (WFServicesReg.exe) je samostatný nástroj, který slouží k přidání, odebrání nebo opravte elementů konfigurace pro služby Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="5b1df-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b1df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b1df-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="5b1df-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b1df-105">Remarks</span></span>  
 <span data-ttu-id="5b1df-106">Nástroj lze nalézt v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] umístění instalace, konkrétně % windir%\Microsoft.NET\Framework\v3.5, nebo na %windir%\Microsoft.NET\Framework64\v3.5 v 64bitových počítačích.</span><span class="sxs-lookup"><span data-stu-id="5b1df-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="5b1df-107">Následující tabulky popisují požadované možnosti, které je možné pomocí nástroje pro registraci služby pracovních postupů (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="5b1df-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="5b1df-108">Možnost</span><span class="sxs-lookup"><span data-stu-id="5b1df-108">Option</span></span>|<span data-ttu-id="5b1df-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5b1df-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="5b1df-110">Nakonfiguruje služby pracovního postupu Windows.</span><span class="sxs-lookup"><span data-stu-id="5b1df-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="5b1df-111">Při instalaci a opravte scénáře.</span><span class="sxs-lookup"><span data-stu-id="5b1df-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="5b1df-112">Odebere konfigurace služby pracovního postupu Windows.</span><span class="sxs-lookup"><span data-stu-id="5b1df-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="5b1df-113">Vytisknout podrobné informace (pro konfiguraci nebo odebrání).</span><span class="sxs-lookup"><span data-stu-id="5b1df-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="5b1df-114">Povolí formát protokolování MSI.</span><span class="sxs-lookup"><span data-stu-id="5b1df-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="5b1df-115">Minimalizuje okno při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b1df-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="5b1df-116">Registrace</span><span class="sxs-lookup"><span data-stu-id="5b1df-116">Registration</span></span>  
 <span data-ttu-id="5b1df-117">Nástroj zkontroluje v souboru Web.config a zaregistruje následující:</span><span class="sxs-lookup"><span data-stu-id="5b1df-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <span data-ttu-id="5b1df-118">referenční sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b1df-118">reference assemblies.</span></span>  
  
- <span data-ttu-id="5b1df-119">Sestavení zprostředkovatele pro soubory XOML.</span><span class="sxs-lookup"><span data-stu-id="5b1df-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="5b1df-120">Obslužné rutiny HTTP pro soubory XOML a .rules.</span><span class="sxs-lookup"><span data-stu-id="5b1df-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="5b1df-121">Nástroj zkontroluje soubor Machine.config a registruje následující rozšíření:</span><span class="sxs-lookup"><span data-stu-id="5b1df-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="5b1df-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="5b1df-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="5b1df-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="5b1df-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="5b1df-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="5b1df-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="5b1df-125">Nástroj také zaregistruje následující metadata importers klienta:</span><span class="sxs-lookup"><span data-stu-id="5b1df-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="5b1df-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="5b1df-126">policyImporters</span></span>  
  
- <span data-ttu-id="5b1df-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="5b1df-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="5b1df-128">Nástroj také zaregistruje XOML a .rules mapy skriptů a obslužné rutiny v metabázi služby IIS.</span><span class="sxs-lookup"><span data-stu-id="5b1df-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="5b1df-129">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)] počítače (služba IIS 5.1 a [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jedna sada XOML a .rules mapy skriptů jsou registrované.</span><span class="sxs-lookup"><span data-stu-id="5b1df-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="5b1df-130">Na 64bitových počítačích, nástroj zaregistruje mapy skriptů režimu WOW, pokud `Enable32BitAppOnWin64` přepínač je povolený, nebo nativní 64bitové mapy skriptů, pokud `Enable32BitAppOnWin64` přepínač je zakázaný.</span><span class="sxs-lookup"><span data-stu-id="5b1df-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="5b1df-131">Na [!INCLUDE[wv](../../../includes/wv-md.md)] a Windows Server 2008 (služba IIS 7.0 a vyšší) počítače, dvě sady XOML a .rules obslužné rutiny jsou registrovány: jeden pro integrovaný režim a jeden pro klasický režim.</span><span class="sxs-lookup"><span data-stu-id="5b1df-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="5b1df-132">Na 64bitových počítačích jsou registrovány tři páry obslužné rutiny (bez ohledu na stav `Enable32BitAppOnWin64` přepnout): jeden pro integrovaný režim, jeden pro WOW klasického režimu a jeden pro nativní 64bitové klasickém režimu.</span><span class="sxs-lookup"><span data-stu-id="5b1df-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b1df-133">Na rozdíl od ServiceModelreg.exe WFServicesReg.exe neumožňuje přidání, odebrání nebo oprava mapování skriptů nebo obslužné rutiny pro určitý web.</span><span class="sxs-lookup"><span data-stu-id="5b1df-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="5b1df-134">Alternativní řešení těchto potíží najdete v části "Oprava the mapy skriptů".</span><span class="sxs-lookup"><span data-stu-id="5b1df-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="5b1df-135">Scénáře použití</span><span class="sxs-lookup"><span data-stu-id="5b1df-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="5b1df-136">Instalace služby IIS po instalaci rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="5b1df-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="5b1df-137">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítače, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] nainstalovaný před instalací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="5b1df-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="5b1df-138">Kvůli nedostupnosti metabáze služby IIS, instalaci [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bude úspěšné bez instalace XOML a .rules mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="5b1df-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="5b1df-139">Po instalaci služby IIS, můžete použít nástroj WFServicesReg.exe s `/c` přepínač k instalaci těchto konkrétních mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="5b1df-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="5b1df-140">Oprava mapování skriptů</span><span class="sxs-lookup"><span data-stu-id="5b1df-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="5b1df-141">Odstranit pod uzlem weby v mapě skriptů</span><span class="sxs-lookup"><span data-stu-id="5b1df-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="5b1df-142">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules náhodně odstraní ze uzel weby.</span><span class="sxs-lookup"><span data-stu-id="5b1df-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="5b1df-143">To lze opravit spuštěním nástroje WFServicesReg.exe s `/c` přepnout.</span><span class="sxs-lookup"><span data-stu-id="5b1df-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="5b1df-144">Mapování skriptů odstranit v rámci určitého webového serveru</span><span class="sxs-lookup"><span data-stu-id="5b1df-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="5b1df-145">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules náhodně odstraní z určitého webového serveru (například výchozí web), nikoli z uzlu webových serverů.</span><span class="sxs-lookup"><span data-stu-id="5b1df-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="5b1df-146">K opravě odstraněné obslužné rutiny pro určitý web, měli byste spustit "WFServicesReg.exe r" k odebrání obslužných rutin ze všech webů, spusťte "WFServicesReg.exe c" k vytvoření odpovídající obslužné rutiny pro všechny weby.</span><span class="sxs-lookup"><span data-stu-id="5b1df-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="5b1df-147">Konfigurace obslužné rutiny po změně režimu služby IIS</span><span class="sxs-lookup"><span data-stu-id="5b1df-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="5b1df-148">Když služba IIS pracuje v režimu sdílenou konfiguraci a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalovaný, metabáze služby IIS je nakonfigurované v rámci sdílené umístění.</span><span class="sxs-lookup"><span data-stu-id="5b1df-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="5b1df-149">Pokud přepnete do režimu bez sdílená konfigurace služby IIS, nebude obsahovat místní metabáze požadované obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="5b1df-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="5b1df-150">Pokud chcete nakonfigurovat místní metabáze správně, můžete buď importovat sdílené metabáze na místní nebo spuštění "WFServicesReg.exe /c", který konfiguruje místní metabáze.</span><span class="sxs-lookup"><span data-stu-id="5b1df-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
