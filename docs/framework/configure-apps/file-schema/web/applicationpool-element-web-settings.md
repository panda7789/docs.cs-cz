---
title: '&lt;applicationPool&gt; – Element (webové nastavení)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2eafc6b5ad1446fd07518f877a8ec001ad8dbd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltapplicationpoolgt-element-web-settings"></a><span data-ttu-id="7fcba-102">&lt;applicationPool&gt; – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="7fcba-102">&lt;applicationPool&gt; Element (Web Settings)</span></span>
<span data-ttu-id="7fcba-103">Určuje nastavení konfigurace, které jsou používány ASP.NET ke správě procesy chování, když aplikace ASP.NET běží v integrovaném režimu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="7fcba-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fcba-104">Tento prvek a funkci podporuje funguje jenom v případě, že je vaše aplikace ASP.NET hostované na [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="7fcba-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="7fcba-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7fcba-105">\<configuration></span></span>  
<span data-ttu-id="7fcba-106">\<System.Web > elementu (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="7fcba-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="7fcba-107">\<applicationPool > – Element (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="7fcba-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fcba-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fcba-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fcba-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7fcba-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7fcba-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7fcba-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fcba-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7fcba-111">Attributes</span></span>  
  
|<span data-ttu-id="7fcba-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="7fcba-112">Attribute</span></span>|<span data-ttu-id="7fcba-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7fcba-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="7fcba-114">Určuje, kolik souběžných požadavků ASP.NET umožňuje za využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="7fcba-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="7fcba-115">Určuje, kolik souběžných vláken můžete používat pro fond aplikací pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="7fcba-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="7fcba-116">To poskytuje alternativní způsob řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, které lze použít na procesoru k obsluze požadavků.</span><span class="sxs-lookup"><span data-stu-id="7fcba-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="7fcba-117">Ve výchozím nastavení toto nastavení je 0, což znamená, že technologie ASP.NET neomezuje počet vláken, které lze vytvořit na procesor, i když fondu vláken CLR také omezuje počet vláken, které lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7fcba-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="7fcba-118">Určuje maximální počet požadavků, které lze zařadit do fronty pro technologii ASP.NET v jediném procesu.</span><span class="sxs-lookup"><span data-stu-id="7fcba-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="7fcba-119">Pokud dva nebo více aplikací ASP.NET spustit v jeden fond aplikací, podléhá úhrnnou sadu oprav požadavkům na všechny aplikace ve fondu aplikací, toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="7fcba-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fcba-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7fcba-120">Child Elements</span></span>  
 <span data-ttu-id="7fcba-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="7fcba-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7fcba-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7fcba-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7fcba-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7fcba-123">Element</span></span>|<span data-ttu-id="7fcba-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7fcba-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fcba-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="7fcba-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="7fcba-126">Obsahuje informace o spolupráci ASP.NET s hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7fcba-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fcba-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fcba-127">Remarks</span></span>  
 <span data-ttu-id="7fcba-128">Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace element vám umožní nakonfigurovat jak ASP.NET spravuje vláken a fronty požadavků, když je aplikace hostované ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7fcba-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="7fcba-129">Je-li spustit služby IIS 6 nebo ji spustit [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] v klasickém režimu nebo v režimu ISAPI, tato nastavení ignorují.</span><span class="sxs-lookup"><span data-stu-id="7fcba-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="7fcba-130">`applicationPool` Nastavení se vztahují na všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7fcba-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="7fcba-131">Nastavení jsou obsaženy v souboru Soubor aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="7fcba-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="7fcba-132">Je verze tohoto souboru pro verze 2.0 a rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="7fcba-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="7fcba-133">(Verze 3.0 a rozhraní .NET Framework 3.5 sdílet s verze 2.0 Soubor aspnet.config.)</span><span class="sxs-lookup"><span data-stu-id="7fcba-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fcba-134">Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete nakonfigurovat samostatný soubor aspnet.config soubor pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="7fcba-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="7fcba-135">Díky tomu můžete přizpůsobit výkon vláken pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="7fcba-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="7fcba-136">Pro `maxConcurrentRequestsPerCPU` nastavení, výchozí nastavení "5 000" v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] omezení požadavků efektivně vypne řízené ASP.NET, pokud máte ve skutečnosti 5000 nebo další požadavky na procesor.</span><span class="sxs-lookup"><span data-stu-id="7fcba-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="7fcba-137">Výchozí nastavení, místo toho závisí na CLR-fondu vláken automaticky spravovat souběžnosti za využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="7fcba-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="7fcba-138">Aplikace, které usnadňují rozsáhlé používání asynchronní zpracování požadavků nebo které mají mnoho požadavků dlouho běžící zablokovaných v síti vstupně-výstupních operací, bude využívat vyšší výchozí limit v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7fcba-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="7fcba-139">Nastavení `maxConcurrentRequestsPerCPU` na nulové vypne používání spravovaných vláken pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7fcba-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="7fcba-140">Když aplikace běží v fond aplikací služby IIS, požadavky Zůstaňte na vlákno vstupně-výstupních operací služby IIS a proto je omezené souběžnosti vláken nastavení služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7fcba-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="7fcba-141">`requestQueueLimit` Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, který je nastaven v souborech Web.config pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7fcba-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="7fcba-142">Ale `requestQueueLimit` přepíše nastavení v souboru aspnet.config `requestQueueLimit` nastavení v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="7fcba-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="7fcba-143">Jinými slovy Pokud jsou oba atributy (ve výchozím nastavení, to je true), `requestQueueLimit` přednost má nastavení v souboru Soubor aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="7fcba-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fcba-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fcba-144">Example</span></span>  
 <span data-ttu-id="7fcba-145">Následující příklad ukazuje, jak nakonfigurovat chování procesy ASP.NET v souboru aspnet.config v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="7fcba-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
-   <span data-ttu-id="7fcba-146">Aplikace je hostován v [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="7fcba-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]<span data-ttu-id="7fcba-147"> je spuštěna v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="7fcba-147"> is running in Integrated mode.</span></span>  
  
-   <span data-ttu-id="7fcba-148">Aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.</span><span class="sxs-lookup"><span data-stu-id="7fcba-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="7fcba-149">Hodnoty v příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7fcba-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="7fcba-150">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="7fcba-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fcba-151">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7fcba-151">Namespace</span></span>||  
|<span data-ttu-id="7fcba-152">Název schématu</span><span class="sxs-lookup"><span data-stu-id="7fcba-152">Schema Name</span></span>||  
|<span data-ttu-id="7fcba-153">Ověření souboru</span><span class="sxs-lookup"><span data-stu-id="7fcba-153">Validation File</span></span>||  
|<span data-ttu-id="7fcba-154">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="7fcba-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="7fcba-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fcba-155">See Also</span></span>  
 [<span data-ttu-id="7fcba-156">\<System.Web > elementu (webové nastavení)</span><span class="sxs-lookup"><span data-stu-id="7fcba-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
