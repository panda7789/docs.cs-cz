---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: f0486e9faf70e7d5d147cfef996edcdaa8846963
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456292"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="b5827-102">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="b5827-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="b5827-103">Určuje nastavení konfigurace, který ASP.NET používá ke správě celého procesu chování, když aplikaci ASP.NET běží v integrovaném režimu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b5827-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5827-104">Tento element a funkci podporuje fungovat, pouze pokud je hostitelem aplikace technologie ASP.NET [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="b5827-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="b5827-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="b5827-105">\<configuration></span></span>  
<span data-ttu-id="b5827-106">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="b5827-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="b5827-107">\<applicationPool > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="b5827-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5827-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5827-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5827-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b5827-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b5827-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b5827-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5827-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b5827-111">Attributes</span></span>  
  
|<span data-ttu-id="b5827-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="b5827-112">Attribute</span></span>|<span data-ttu-id="b5827-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b5827-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="b5827-114">Určuje, kolik souběžných požadavků ASP.NET umožňuje jeden procesor.</span><span class="sxs-lookup"><span data-stu-id="b5827-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="b5827-115">Určuje, kolik souběžných vláken může být spuštěn fond aplikací, pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="b5827-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="b5827-116">To poskytuje alternativní způsob řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, které můžete použít jeden procesor a jsou k obsluze požadavků.</span><span class="sxs-lookup"><span data-stu-id="b5827-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="b5827-117">Ve výchozím nastavení toto nastavení je 0, což znamená, že technologie ASP.NET neomezuje počet vláken, která je možné vytvořit jeden procesor, i když fondu vláken CLR také omezuje počet vláken, která je možné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b5827-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="b5827-118">Určuje maximální počet požadavků, které lze zařadit do fronty pro technologii ASP.NET v jediném procesu.</span><span class="sxs-lookup"><span data-stu-id="b5827-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="b5827-119">Když dva nebo více aplikací ASP.NET spustit v jediného fondu aplikací, můžou toto nastavení je kumulativní sadu požadavky na všechny aplikace ve fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5827-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5827-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b5827-120">Child Elements</span></span>  
 <span data-ttu-id="b5827-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b5827-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5827-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b5827-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5827-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b5827-123">Element</span></span>|<span data-ttu-id="b5827-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b5827-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5827-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="b5827-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="b5827-126">Obsahuje informace o způsobu interakce ASP.NET s hostitelskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5827-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5827-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5827-127">Remarks</span></span>  
 <span data-ttu-id="b5827-128">Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace elementu vám umožní nakonfigurovat jak ASP.NET spravuje vláken a fronty požadavků, když je aplikace hostovaná ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="b5827-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="b5827-129">Je-li spustit služby IIS 6 nebo spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] v klasickém režimu nebo v režimu ISAPI, tato nastavení jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="b5827-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="b5827-130">`applicationPool` Nastavení platí pro všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5827-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="b5827-131">Nastavení jsou obsaženy v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="b5827-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="b5827-132">Existuje verze tohoto souboru pro verze 2.0, 4.0 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5827-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="b5827-133">(Verze 3.0 a 3.5 rozhraní .NET Framework sdílet s verzí 2.0 Soubor aspnet.config.)</span><span class="sxs-lookup"><span data-stu-id="b5827-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5827-134">Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete nakonfigurovat samostatný aspnet.config souboru pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5827-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="b5827-135">Díky tomu můžete přizpůsobit výkonu vláken pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5827-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="b5827-136">Pro `maxConcurrentRequestsPerCPU` nastavení, ve výchozím nastavení "5000" v rozhraní .NET Framework 4 efektivně vypne omezování žádostí, které je řízen pomocí technologie ASP.NET, pokud máte ve skutečnosti 5000 nebo více požadavků na CPU.</span><span class="sxs-lookup"><span data-stu-id="b5827-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="b5827-137">Ve výchozím nastavení závisí na modulu CLR-fondu vláken k automatické správě souběžnosti jeden procesor a místo toho.</span><span class="sxs-lookup"><span data-stu-id="b5827-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="b5827-138">Aplikace, které usnadňují používání příliš často používá asynchronní zpracování požadavků, nebo jež mají velký počet požadavků dlouhotrvající blokován v síti vstupně-výstupních operací, bude využít zvýšenou výchozí limit v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b5827-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="b5827-139">Nastavení `maxConcurrentRequestsPerCPU` na nulovou vypne použití spravovaných vláken pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5827-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="b5827-140">Pokud je aplikace spuštěna ve fondu aplikací služby IIS, požadavky zůstat ve vlákně vstupně-výstupních operací služby IIS a proto se omezuje souběžnosti vláken nastavením služby IIS.</span><span class="sxs-lookup"><span data-stu-id="b5827-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="b5827-141">`requestQueueLimit` Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, který je nastavení v souborech Web.config pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5827-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="b5827-142">Ale `requestQueueLimit` přepíše nastavení v souboru aspnet.config `requestQueueLimit` nastavení v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="b5827-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="b5827-143">Jinými slovy Pokud oba atributy jsou nastavené (ve výchozím nastavení, to je PRAVDA), `requestQueueLimit` přednost má nastavení v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="b5827-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5827-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5827-144">Example</span></span>  
 <span data-ttu-id="b5827-145">Následující příklad ukazuje, jak nakonfigurovat chování v celém procesu ASP.NET v souboru aspnet.config za následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="b5827-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="b5827-146">Aplikace je hostována v [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="b5827-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
- [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="b5827-147">běží v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="b5827-147">is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="b5827-148">Aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b5827-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="b5827-149">Hodnoty v tomto příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5827-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="b5827-150">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="b5827-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5827-151">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b5827-151">Namespace</span></span>||  
|<span data-ttu-id="b5827-152">Název schématu</span><span class="sxs-lookup"><span data-stu-id="b5827-152">Schema Name</span></span>||  
|<span data-ttu-id="b5827-153">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="b5827-153">Validation File</span></span>||  
|<span data-ttu-id="b5827-154">Může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="b5827-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="b5827-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5827-155">See also</span></span>

- [<span data-ttu-id="b5827-156">\<System.Web > – Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="b5827-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
