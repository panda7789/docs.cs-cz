---
title: <applicationPool> – element (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: a9c81d98a5e531eaa547614c4d236b6c84526398
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758271"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="d7c86-102">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="d7c86-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="d7c86-103">Určuje nastavení konfigurace, který ASP.NET používá ke správě celého procesu chování, když aplikaci ASP.NET běží v integrovaném režimu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d7c86-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7c86-104">Tento element a funkci podporuje fungovat, pouze pokud je hostitelem aplikace technologie ASP.NET [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="d7c86-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="d7c86-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d7c86-105">\<configuration></span></span>  
<span data-ttu-id="d7c86-106">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="d7c86-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="d7c86-107">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="d7c86-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c86-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7c86-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7c86-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d7c86-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d7c86-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d7c86-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7c86-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d7c86-111">Attributes</span></span>  
  
|<span data-ttu-id="d7c86-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d7c86-112">Attribute</span></span>|<span data-ttu-id="d7c86-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d7c86-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="d7c86-114">Určuje, kolik souběžných požadavků ASP.NET umožňuje jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="d7c86-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="d7c86-115">Určuje, kolik souběžných vláken může být spuštěn fond aplikací, pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="d7c86-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="d7c86-116">To poskytuje alternativní způsob řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, které můžete použít jeden procesor a jsou k obsluze požadavků.</span><span class="sxs-lookup"><span data-stu-id="d7c86-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="d7c86-117">Ve výchozím nastavení toto nastavení je 0, což znamená, že technologie ASP.NET neomezuje počet vláken, která je možné vytvořit jeden procesor, i když fondu vláken CLR také omezuje počet vláken, která je možné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="d7c86-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="d7c86-118">Určuje maximální počet požadavků, které lze zařadit do fronty pro technologii ASP.NET v jediném procesu.</span><span class="sxs-lookup"><span data-stu-id="d7c86-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="d7c86-119">Když dva nebo více aplikací ASP.NET spustit v jediného fondu aplikací, můžou toto nastavení je kumulativní sadu požadavky na všechny aplikace ve fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7c86-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7c86-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d7c86-120">Child Elements</span></span>  
 <span data-ttu-id="d7c86-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="d7c86-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7c86-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d7c86-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d7c86-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7c86-123">Element</span></span>|<span data-ttu-id="d7c86-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d7c86-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7c86-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="d7c86-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="d7c86-126">Obsahuje informace o způsobu interakce ASP.NET s hostitelskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7c86-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7c86-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7c86-127">Remarks</span></span>  
 <span data-ttu-id="d7c86-128">Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace elementu vám umožní nakonfigurovat jak ASP.NET spravuje vláken a fronty požadavků, když je aplikace hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d7c86-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="d7c86-129">Je-li spustit služby IIS 6 nebo spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] v klasickém režimu nebo v režimu ISAPI, tato nastavení jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="d7c86-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="d7c86-130">`applicationPool` Nastavení platí pro všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c86-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="d7c86-131">Nastavení jsou obsaženy v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="d7c86-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="d7c86-132">Existuje verze tohoto souboru pro verze 2.0, 4.0 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d7c86-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="d7c86-133">(Verze 3.0 a 3.5 rozhraní .NET Framework sdílet s verzí 2.0 Soubor aspnet.config.)</span><span class="sxs-lookup"><span data-stu-id="d7c86-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7c86-134">Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete nakonfigurovat samostatný aspnet.config souboru pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7c86-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="d7c86-135">Díky tomu můžete přizpůsobit výkonu vláken pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7c86-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="d7c86-136">Pro `maxConcurrentRequestsPerCPU` nastavení, ve výchozím nastavení "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] efektivně vypne omezování žádostí, který je řízen technologie ASP.NET, pokud máte ve skutečnosti 5000 nebo více požadavků na CPU.</span><span class="sxs-lookup"><span data-stu-id="d7c86-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="d7c86-137">Ve výchozím nastavení závisí na modulu CLR-fondu vláken k automatické správě souběžnosti jeden procesor a místo toho.</span><span class="sxs-lookup"><span data-stu-id="d7c86-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="d7c86-138">Aplikace, které usnadňují používání příliš často používá asynchronní zpracování požadavků, nebo jež mají velký počet požadavků dlouhotrvající blokován v síti vstupně-výstupních operací, bude využívat zvýšení výchozí limit v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d7c86-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="d7c86-139">Nastavení `maxConcurrentRequestsPerCPU` na nulovou vypne použití spravovaných vláken pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d7c86-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="d7c86-140">Pokud je aplikace spuštěna ve fondu aplikací služby IIS, požadavky zůstat ve vlákně vstupně-výstupních operací služby IIS a proto se omezuje souběžnosti vláken nastavením služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d7c86-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="d7c86-141">`requestQueueLimit` Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, který je nastavení v souborech Web.config pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d7c86-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="d7c86-142">Ale `requestQueueLimit` přepíše nastavení v souboru aspnet.config `requestQueueLimit` nastavení v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="d7c86-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="d7c86-143">Jinými slovy Pokud oba atributy jsou nastavené (ve výchozím nastavení, to je PRAVDA), `requestQueueLimit` přednost má nastavení v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="d7c86-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c86-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7c86-144">Example</span></span>  
 <span data-ttu-id="d7c86-145">Následující příklad ukazuje, jak nakonfigurovat chování v celém procesu ASP.NET v souboru aspnet.config za následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="d7c86-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
-   <span data-ttu-id="d7c86-146">Aplikace je hostována v [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="d7c86-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="d7c86-147">běží v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="d7c86-147">is running in Integrated mode.</span></span>  
  
-   <span data-ttu-id="d7c86-148">Aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d7c86-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="d7c86-149">Hodnoty v tomto příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d7c86-149">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="d7c86-150">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="d7c86-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7c86-151">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d7c86-151">Namespace</span></span>||  
|<span data-ttu-id="d7c86-152">Název schématu</span><span class="sxs-lookup"><span data-stu-id="d7c86-152">Schema Name</span></span>||  
|<span data-ttu-id="d7c86-153">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="d7c86-153">Validation File</span></span>||  
|<span data-ttu-id="d7c86-154">Může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="d7c86-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="d7c86-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7c86-155">See also</span></span>
- [<span data-ttu-id="d7c86-156">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="d7c86-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
