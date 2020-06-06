---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152851"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="7afd3-102">Element \<applicationPool> (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="7afd3-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="7afd3-103">Určuje nastavení konfigurace, které ASP.NET používá ke správě chování v rámci procesu, když je aplikace ASP.NET spuštěná v integrovaném režimu na IIS 7,0 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="7afd3-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7afd3-104">Tento prvek a funkce, které podporuje, fungují pouze v případě, že je vaše aplikace ASP.NET hostována ve službě IIS 7,0 nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="7afd3-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="7afd3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7afd3-105">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7afd3-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7afd3-106">Attributes and Elements</span></span>  

<span data-ttu-id="7afd3-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7afd3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7afd3-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="7afd3-108">Attributes</span></span>  
  
|<span data-ttu-id="7afd3-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="7afd3-109">Attribute</span></span>|<span data-ttu-id="7afd3-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7afd3-110">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="7afd3-111">Určuje, kolik souběžných požadavků ASP.NET povoluje jednotlivé PROCESORy.</span><span class="sxs-lookup"><span data-stu-id="7afd3-111">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="7afd3-112">Určuje, kolik souběžných vláken může být spuštěno pro fond aplikací pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="7afd3-112">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="7afd3-113">To poskytuje alternativní způsob pro řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, která lze použít pro jednotlivé PROCESORy k obsluze požadavků.</span><span class="sxs-lookup"><span data-stu-id="7afd3-113">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="7afd3-114">Ve výchozím nastavení je toto nastavení 0, což znamená, že ASP.NET neomezuje počet vláken, která lze vytvořit pro jednotlivé PROCESORy, i když fond vláken CLR také omezuje počet vláken, která lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="7afd3-114">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="7afd3-115">Určuje maximální počet požadavků, které mohou být zařazeny do fronty pro ASP.NET v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="7afd3-115">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="7afd3-116">V případě, že dvě nebo více ASP.NETch aplikací běží v jednom fondu aplikací, toto nastavení se vztahuje na kumulativní sadu požadavků, které se přidávají do jakékoli aplikace ve fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="7afd3-116">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7afd3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7afd3-117">Child Elements</span></span>  
 <span data-ttu-id="7afd3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="7afd3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7afd3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7afd3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7afd3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="7afd3-120">Element</span></span>|<span data-ttu-id="7afd3-121">Description</span><span class="sxs-lookup"><span data-stu-id="7afd3-121">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="7afd3-122">Obsahuje informace o tom, jak ASP.NET komunikuje s hostitelskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="7afd3-122">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7afd3-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7afd3-123">Remarks</span></span>  

<span data-ttu-id="7afd3-124">Pokud spustíte službu IIS 7,0 nebo novější verzi v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a fronty, když je aplikace hostována ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="7afd3-124">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="7afd3-125">Pokud spouštíte IIS 6 nebo v klasickém režimu nebo v režimu ISAPI spouštíte IIS 7,0, tato nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="7afd3-125">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="7afd3-126">`applicationPool`Nastavení platí pro všechny fondy aplikací, které běží na konkrétní verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7afd3-126">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="7afd3-127">Nastavení jsou obsažena v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="7afd3-127">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="7afd3-128">Verze tohoto souboru je verze 2,0 a 4,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7afd3-128">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="7afd3-129">(Verze 3,0 a 3,5 .NET Framework sdílet soubor ASPNET. config s verzí 2,0.)</span><span class="sxs-lookup"><span data-stu-id="7afd3-129">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7afd3-130">Pokud ve Windows 7 spustíte IIS 7,0, můžete pro každý fond aplikací nakonfigurovat samostatný soubor ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="7afd3-130">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="7afd3-131">To vám umožní přizpůsobit výkon vláken pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="7afd3-131">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="7afd3-132">V případě `maxConcurrentRequestsPerCPU` nastavení výchozí nastavení "5000" v .NET Framework 4 efektivně vypne omezení požadavků, které je řízeno ASP.NETou, pokud ve skutečnosti nemáte 5000 nebo více požadavků na procesor.</span><span class="sxs-lookup"><span data-stu-id="7afd3-132">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="7afd3-133">Výchozí nastavení závisí na fondu vláken CLR k automatické správě souběžnosti na procesor.</span><span class="sxs-lookup"><span data-stu-id="7afd3-133">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="7afd3-134">Aplikace, které vytvářejí rozsáhlé použití asynchronního zpracování požadavků nebo které mají v síťové vstupně-výstupní operaci blokované množství dlouhotrvajících požadavků, budou těžit z zvýšeného výchozího limitu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7afd3-134">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="7afd3-135">Nastavení `maxConcurrentRequestsPerCPU` na hodnotu nula vypne používání spravovaných vláken pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7afd3-135">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="7afd3-136">Když je aplikace spuštěná ve fondu aplikací služby IIS, požadavky zůstanou ve vstupně-výstupních vláknech služby IIS a proto souběžnost je omezena nastavením vlákna IIS.</span><span class="sxs-lookup"><span data-stu-id="7afd3-136">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="7afd3-137">`requestQueueLimit`Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut prvku [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , který je nastaven v souborech Web. config pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7afd3-137">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="7afd3-138">`requestQueueLimit`Nastavení v souboru ASPNET. config však přepisuje `requestQueueLimit` nastavení v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="7afd3-138">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="7afd3-139">Jinými slovy, pokud jsou oba atributy nastaveny (ve výchozím nastavení je to pravda), `requestQueueLimit` má přednost nastavení v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="7afd3-139">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7afd3-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="7afd3-140">Example</span></span>  

<span data-ttu-id="7afd3-141">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="7afd3-141">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="7afd3-142">Aplikace je hostována ve fondu aplikací služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="7afd3-142">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="7afd3-143">Služba IIS 7,0 je spuštěna v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="7afd3-143">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="7afd3-144">Aplikace používá .NET Framework 3,5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="7afd3-144">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="7afd3-145">Hodnoty v příkladu jsou výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7afd3-145">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="7afd3-146">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="7afd3-146">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7afd3-147">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7afd3-147">Namespace</span></span>||  
|<span data-ttu-id="7afd3-148">Název schématu</span><span class="sxs-lookup"><span data-stu-id="7afd3-148">Schema Name</span></span>||  
|<span data-ttu-id="7afd3-149">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="7afd3-149">Validation File</span></span>||  
|<span data-ttu-id="7afd3-150">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="7afd3-150">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="7afd3-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="7afd3-151">See also</span></span>

- [<span data-ttu-id="7afd3-152">\<system.web>– Element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="7afd3-152">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
