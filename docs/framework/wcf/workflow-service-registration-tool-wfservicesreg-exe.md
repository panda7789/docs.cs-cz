---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: cf5ea345c900dec0e4859d81fcb272c1ba3d3df6
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837750"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="6b2bb-102">Nástroj WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="6b2bb-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="6b2bb-103">Nástroj pro registraci služby Workflow Services (WFServicesReg. exe) je samostatný nástroj, který se dá použít k přidání, odebrání nebo opravě elementů konfigurace pro služby programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="6b2bb-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b2bb-104">Syntax</span></span>  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b2bb-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b2bb-105">Remarks</span></span>  
 <span data-ttu-id="6b2bb-106">Tento nástroj najdete v umístění instalace .NET Framework 3,5, konkrétně na%windir%\Microsoft.NET\Framework\v3.5 nebo na%windir%\Microsoft.NET\Framework64\v3.5 v 64 bitové počítače.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-106">The tool can be found at the .NET Framework 3.5 installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="6b2bb-107">Následující tabulky popisují možnosti, které se dají použít s nástrojem pro registraci služby pracovních postupů (WFServicesReg. exe).</span><span class="sxs-lookup"><span data-stu-id="6b2bb-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="6b2bb-108">Možnost</span><span class="sxs-lookup"><span data-stu-id="6b2bb-108">Option</span></span>|<span data-ttu-id="6b2bb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6b2bb-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="6b2bb-110">Konfiguruje služby Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="6b2bb-111">Používá se v scénářích instalace a opravy.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="6b2bb-112">Odebere konfiguraci služby Windows Workflow Services.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="6b2bb-113">Vytiskne podrobné informace o konfiguraci nebo odebrání.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="6b2bb-114">Povolí formát protokolování MSI.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="6b2bb-115">Minimalizuje okno při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="6b2bb-116">Registrace</span><span class="sxs-lookup"><span data-stu-id="6b2bb-116">Registration</span></span>  
 <span data-ttu-id="6b2bb-117">Nástroj zkontroluje soubor Web. config a zaregistruje následující:</span><span class="sxs-lookup"><span data-stu-id="6b2bb-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
- <span data-ttu-id="6b2bb-118">Referenční sestavení .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-118">.NET Framework 3.5 reference assemblies.</span></span>  
  
- <span data-ttu-id="6b2bb-119">Poskytovatel sestavení pro soubory. xoml.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-119">A build provider for .xoml files.</span></span>  
  
- <span data-ttu-id="6b2bb-120">Obslužné rutiny HTTP pro soubory. XOML a. Rules.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="6b2bb-121">Nástroj zkontroluje soubor Machine. config a zaregistruje následující rozšíření:</span><span class="sxs-lookup"><span data-stu-id="6b2bb-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
- <span data-ttu-id="6b2bb-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="6b2bb-122">behaviorExtensions</span></span>  
  
- <span data-ttu-id="6b2bb-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="6b2bb-123">bindingElementExtensions</span></span>  
  
- <span data-ttu-id="6b2bb-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="6b2bb-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="6b2bb-125">Nástroj také zaregistruje následující nástroje pro import metadat klienta:</span><span class="sxs-lookup"><span data-stu-id="6b2bb-125">The tool also registers the following client metadata importers:</span></span>  
  
- <span data-ttu-id="6b2bb-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="6b2bb-126">policyImporters</span></span>  
  
- <span data-ttu-id="6b2bb-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="6b2bb-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="6b2bb-128">Nástroj také zaregistruje mapy skriptů a obslužných rutin v metabázi služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="6b2bb-129">Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)]ch počítačích (IIS 5,1 a IIS 6,0) se zaregistruje jedna sada map. XOML a. Rules.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and IIS 6.0), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="6b2bb-130">V 64 bitových počítačích nástroj zaregistruje v režimu WOW mapy skriptů, pokud je povolený přepínač `Enable32BitAppOnWin64`, nebo nativní 64é mapy skriptů, pokud je přepínač `Enable32BitAppOnWin64` zakázaný.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="6b2bb-131">V počítačích se systémem Windows Vista a Windows Server 2008 (IIS 7,0 a vyšší) jsou registrovány dvě sady obslužných rutin. XOML a. Rules: jeden pro integrovaný režim a jeden pro klasický režim.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-131">On Windows Vista and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="6b2bb-132">Na 64ch bitových počítačích jsou registrovány tři sady obslužných rutin (bez ohledu na stav přepínače `Enable32BitAppOnWin64`): jeden pro integrovaný režim, jeden pro integrovaný režim WOW a jeden pro nativní 64 klasický režim.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b2bb-133">Na rozdíl od ServiceModelreg. exe nepovoluje WFServicesReg. exe přidávání, odebírání ani opravy mapování skriptů nebo obslužných rutin pro konkrétní web.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="6b2bb-134">Alternativní řešení tohoto problému najdete v části "Oprava map skriptů".</span><span class="sxs-lookup"><span data-stu-id="6b2bb-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="6b2bb-135">Scénáře použití</span><span class="sxs-lookup"><span data-stu-id="6b2bb-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="6b2bb-136">Instalace služby IIS po instalaci .NET Framework 3,5</span><span class="sxs-lookup"><span data-stu-id="6b2bb-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="6b2bb-137">V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači se před instalací služby IIS nainstaluje .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .NET Framework 3.5 is installed prior to IIS installation.</span></span> <span data-ttu-id="6b2bb-138">Z důvodu nedostupnosti metabáze služby IIS je instalace .NET Framework 3,5 úspěšná, aniž by bylo potřeba instalovat. XOML a. Rules mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-138">Due to the unavailability of the IIS metabase, installation of .NET Framework 3.5 succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="6b2bb-139">Po instalaci služby IIS můžete použít nástroj WFServicesReg. exe s přepínačem `/c` k instalaci těchto specifických mapování skriptů.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="6b2bb-140">Oprava map skriptů</span><span class="sxs-lookup"><span data-stu-id="6b2bb-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="6b2bb-141">V uzlu weby byly odstraněny mapy skriptů.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="6b2bb-142">V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači,. XOML nebo. Rules se omylem odstraní z uzlu weby.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="6b2bb-143">To lze opravit spuštěním nástroje WFServicesReg. exe s přepínačem `/c`.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="6b2bb-144">Mapování skriptů se odstranilo v rámci určitého webu.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="6b2bb-145">V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači,. XOML nebo. pravidla se náhodně odstraní z konkrétního webu (například z výchozího webu), nikoli z uzlu weby.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="6b2bb-146">Chcete-li opravit odstraněné obslužné rutiny pro konkrétní web, spusťte příkaz "WFServicesReg. exe/r" pro odebrání obslužných rutin ze všech webů a pak spuštěním příkazu "WFServicesReg. exe/c" vytvořte vhodné obslužné rutiny pro všechny weby.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="6b2bb-147">Konfigurace obslužných rutin po přepnutí režimu služby IIS</span><span class="sxs-lookup"><span data-stu-id="6b2bb-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="6b2bb-148">Když je služba IIS v režimu sdílené konfigurace a je nainstalovaná .NET Framework 3,5, je metabáze IIS nakonfigurovaná v rámci sdíleného umístění.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-148">When IIS is in shared configuration mode and .NET Framework 3.5 is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="6b2bb-149">Pokud přepnete službu IIS do nesdíleného konfiguračního režimu, místní metabáze nebude obsahovat požadované obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="6b2bb-150">Chcete-li správně nakonfigurovat místní metabázi, můžete buď importovat sdílenou metabázi do místní, nebo spustit příkaz "WFServicesReg. exe/c", který konfiguruje místní metabázi.</span><span class="sxs-lookup"><span data-stu-id="6b2bb-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
