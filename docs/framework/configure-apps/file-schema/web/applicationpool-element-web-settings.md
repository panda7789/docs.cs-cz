---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152851"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="6db38-102">\<applicationPool> Element (Nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="6db38-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="6db38-103">Určuje nastavení konfigurace, které ASP.NET používá ke správě chování celého procesu, když je aplikace ASP.NET spuštěna v integrovaném režimu ve službě IIS 7.0 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="6db38-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6db38-104">Tento prvek a funkce, kterou podporuje, fungují pouze v případě, že je aplikace ASP.NET hostována ve službě IIS 7.0 nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="6db38-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="6db38-105">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="6db38-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6db38-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6db38-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="6db38-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<aplikacePool>**</span><span class="sxs-lookup"><span data-stu-id="6db38-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6db38-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6db38-108">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6db38-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6db38-109">Attributes and Elements</span></span>  

<span data-ttu-id="6db38-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6db38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6db38-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6db38-111">Attributes</span></span>  
  
|<span data-ttu-id="6db38-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6db38-112">Attribute</span></span>|<span data-ttu-id="6db38-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6db38-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="6db38-114">Určuje, kolik simultánních požadavků ASP.NET umožňuje na procesor.</span><span class="sxs-lookup"><span data-stu-id="6db38-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="6db38-115">Určuje, kolik simultánních podprocesů může být spuštěno pro fond aplikací pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="6db38-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="6db38-116">To poskytuje alternativní způsob, jak řídit ASP.NET souběžnosti, protože můžete omezit počet spravovaných vláken, které lze použít na procesor k poskytování požadavků.</span><span class="sxs-lookup"><span data-stu-id="6db38-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="6db38-117">Ve výchozím nastavení je toto nastavení 0, což znamená, že ASP.NET neomezuje počet podprocesů, které lze vytvořit na procesor, i když fond vláken CLR také omezuje počet podprocesů, které lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6db38-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="6db38-118">Určuje maximální počet požadavků, které mohou být zařazeny do fronty pro ASP.NET v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="6db38-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="6db38-119">Pokud jsou v jednom fondu aplikací spuštěny dvě nebo více ASP.NET aplikací, bude toto nastavení podléhat kumulativní sadě požadavků pro libovolnou aplikaci ve fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="6db38-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6db38-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6db38-120">Child Elements</span></span>  
 <span data-ttu-id="6db38-121">Žádné.</span><span class="sxs-lookup"><span data-stu-id="6db38-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6db38-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6db38-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6db38-123">Element</span><span class="sxs-lookup"><span data-stu-id="6db38-123">Element</span></span>|<span data-ttu-id="6db38-124">Popis</span><span class="sxs-lookup"><span data-stu-id="6db38-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6db38-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="6db38-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="6db38-126">Obsahuje informace o tom, jak ASP.NET spolupracuje s hostitelskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="6db38-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6db38-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6db38-127">Remarks</span></span>  

<span data-ttu-id="6db38-128">Při spuštění služby IIS 7.0 nebo novější verze v integrovaném režimu umožňuje tato kombinace prvků konfigurovat způsob správy ASP.NET požadavků vláken a front, když je aplikace hostována ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6db38-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="6db38-129">Pokud spustíte službu IIS 6 nebo spustíte službu IIS 7.0 v klasickém režimu nebo v režimu ISAPI, budou tato nastavení ignorována.</span><span class="sxs-lookup"><span data-stu-id="6db38-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="6db38-130">Nastavení `applicationPool` platí pro všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6db38-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="6db38-131">Nastavení jsou obsažena v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="6db38-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="6db38-132">Existuje verze tohoto souboru pro verze 2.0 a 4.0 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6db38-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="6db38-133">(Verze 3.0 a 3.5 rozhraní .NET Framework sdílejí soubor aspnet.config s verzí 2.0.)</span><span class="sxs-lookup"><span data-stu-id="6db38-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6db38-134">Pokud v systému Windows 7 spustíte službu IIS 7.0, můžete nakonfigurovat samostatný soubor aspnet.config pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="6db38-134">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="6db38-135">To umožňuje přizpůsobit výkon podprocesů pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="6db38-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="6db38-136">Pro `maxConcurrentRequestsPerCPU` nastavení výchozí nastavení "5000" v rozhraní .NET Framework 4 efektivně vypne omezení požadavků, které je řízeno ASP.NET, pokud ve skutečnosti nemáte 5000 nebo více požadavků na procesor.</span><span class="sxs-lookup"><span data-stu-id="6db38-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="6db38-137">Výchozí nastavení závisí místo toho na fondu vláken CLR, aby automaticky spravoval souběžnost na procesor.</span><span class="sxs-lookup"><span data-stu-id="6db38-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="6db38-138">Aplikace, které rozsáhle využívají zpracování asynchronních požadavků nebo které mají mnoho dlouhotrvajících požadavků blokovaných v síťových vstupně-televizních službách, budou mít prospěch ze zvýšeného výchozího limitu v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6db38-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="6db38-139">Nastavení `maxConcurrentRequestsPerCPU` na nulu vypne použití spravovaných podprocesů pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6db38-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="6db38-140">Pokud je aplikace spuštěna ve fondu aplikací služby IIS, požadavky zůstávají ve vlákně iis V/O, a proto je souběžnost omezena nastavením podprocesu služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6db38-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="6db38-141">Nastavení `requestQueueLimit` funguje stejným způsobem `requestQueueLimit` jako atribut elementu [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) který je nastaven v souborech Web.config pro ASP.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="6db38-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="6db38-142">`requestQueueLimit` Nastavení v souboru aspnet.config však `requestQueueLimit` přepíše nastavení v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="6db38-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="6db38-143">Jinými slovy, pokud jsou nastaveny oba atributy (ve výchozím nastavení je to pravda), `requestQueueLimit` má přednost nastavení v souboru aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="6db38-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db38-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="6db38-144">Example</span></span>  

<span data-ttu-id="6db38-145">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování celého procesu v souboru aspnet.config za následujících okolností:</span><span class="sxs-lookup"><span data-stu-id="6db38-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="6db38-146">Aplikace je hostována ve fondu aplikací služby IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="6db38-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="6db38-147">Službu IIS 7.0 je spuštěna v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="6db38-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="6db38-148">Aplikace používá rozhraní .NET Framework 3.5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="6db38-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="6db38-149">Hodnoty v příkladu jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6db38-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="6db38-150">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="6db38-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6db38-151">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="6db38-151">Namespace</span></span>||  
|<span data-ttu-id="6db38-152">Název schématu</span><span class="sxs-lookup"><span data-stu-id="6db38-152">Schema Name</span></span>||  
|<span data-ttu-id="6db38-153">Ověřovací soubor</span><span class="sxs-lookup"><span data-stu-id="6db38-153">Validation File</span></span>||  
|<span data-ttu-id="6db38-154">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="6db38-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="6db38-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="6db38-155">See also</span></span>

- [<span data-ttu-id="6db38-156">\<system.web> Element (Nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="6db38-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
