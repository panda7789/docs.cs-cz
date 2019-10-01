---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: c88f4e5407e550047eaf0f5c8d0d2924da611e93
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699227"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="ae34c-102">@no__t – 0applicationPool > – element (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="ae34c-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="ae34c-103">Určuje nastavení konfigurace, které ASP.NET používá ke správě chování v rámci procesu, když je aplikace ASP.NET spuštěná v integrovaném režimu na IIS 7,0 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="ae34c-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae34c-104">Tento prvek a funkce, které podporuje, fungují pouze v případě, že je vaše aplikace ASP.NET hostována ve službě IIS 7,0 nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="ae34c-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="ae34c-105"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="ae34c-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ae34c-106">&nbsp; @ no__t-1[ **@no__t -4system. Web >** ](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ae34c-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="ae34c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<applicationPool >**</span><span class="sxs-lookup"><span data-stu-id="ae34c-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae34c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae34c-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae34c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae34c-109">Attributes and Elements</span></span>  

<span data-ttu-id="ae34c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae34c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae34c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae34c-111">Attributes</span></span>  
  
|<span data-ttu-id="ae34c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae34c-112">Attribute</span></span>|<span data-ttu-id="ae34c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ae34c-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="ae34c-114">Určuje, kolik souběžných požadavků ASP.NET povoluje jednotlivé PROCESORy.</span><span class="sxs-lookup"><span data-stu-id="ae34c-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="ae34c-115">Určuje, kolik souběžných vláken může být spuštěno pro fond aplikací pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="ae34c-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="ae34c-116">To poskytuje alternativní způsob pro řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, která lze použít pro jednotlivé PROCESORy k obsluze požadavků.</span><span class="sxs-lookup"><span data-stu-id="ae34c-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="ae34c-117">Ve výchozím nastavení je toto nastavení 0, což znamená, že ASP.NET neomezuje počet vláken, která lze vytvořit pro jednotlivé PROCESORy, i když fond vláken CLR také omezuje počet vláken, která lze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ae34c-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="ae34c-118">Určuje maximální počet požadavků, které mohou být zařazeny do fronty pro ASP.NET v jednom procesu.</span><span class="sxs-lookup"><span data-stu-id="ae34c-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="ae34c-119">V případě, že dvě nebo více ASP.NETch aplikací běží v jednom fondu aplikací, toto nastavení se vztahuje na kumulativní sadu požadavků, které se přidávají do jakékoli aplikace ve fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae34c-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae34c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae34c-120">Child Elements</span></span>  
 <span data-ttu-id="ae34c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae34c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae34c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae34c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ae34c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae34c-123">Element</span></span>|<span data-ttu-id="ae34c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ae34c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae34c-125">@no__t -1System. Web ></span><span class="sxs-lookup"><span data-stu-id="ae34c-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="ae34c-126">Obsahuje informace o tom, jak ASP.NET komunikuje s hostitelskou aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae34c-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae34c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae34c-127">Remarks</span></span>  

<span data-ttu-id="ae34c-128">Pokud spustíte službu IIS 7,0 nebo novější verzi v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a fronty, když je aplikace hostována ve fondu aplikací služby IIS.</span><span class="sxs-lookup"><span data-stu-id="ae34c-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="ae34c-129">Pokud spouštíte IIS 6 nebo v klasickém režimu nebo v režimu ISAPI spouštíte IIS 7,0, tato nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="ae34c-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="ae34c-130">Nastavení `applicationPool` platí pro všechny fondy aplikací, které běží na konkrétní verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae34c-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="ae34c-131">Nastavení jsou obsažena v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="ae34c-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="ae34c-132">Verze tohoto souboru je verze 2,0 a 4,0 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ae34c-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="ae34c-133">(Verze 3,0 a 3,5 .NET Framework sdílet soubor ASPNET. config s verzí 2,0.)</span><span class="sxs-lookup"><span data-stu-id="ae34c-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae34c-134">Spouštíte-li službu IIS 7,0 na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete pro každý fond aplikací nakonfigurovat samostatný soubor ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="ae34c-134">If you run IIS 7.0 on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="ae34c-135">To vám umožní přizpůsobit výkon vláken pro každý fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="ae34c-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="ae34c-136">U nastavení `maxConcurrentRequestsPerCPU` je ve výchozím nastavení "5000" v .NET Framework 4 účinně vypnuté omezení požadavků, které je řízeno ASP.NETou, pokud ve skutečnosti nemáte 5000 nebo více požadavků na procesor.</span><span class="sxs-lookup"><span data-stu-id="ae34c-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="ae34c-137">Výchozí nastavení závisí na fondu vláken CLR k automatické správě souběžnosti na procesor.</span><span class="sxs-lookup"><span data-stu-id="ae34c-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="ae34c-138">Aplikace, které vytvářejí rozsáhlé použití asynchronního zpracování požadavků nebo které mají v síťové vstupně-výstupní operaci blokované množství dlouhotrvajících požadavků, budou těžit z zvýšeného výchozího limitu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ae34c-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="ae34c-139">Nastavení `maxConcurrentRequestsPerCPU` na hodnotu nula vypne používání spravovaných vláken pro zpracování požadavků ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ae34c-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="ae34c-140">Když je aplikace spuštěná ve fondu aplikací služby IIS, požadavky zůstanou ve vstupně-výstupních vláknech služby IIS a proto souběžnost je omezena nastavením vlákna IIS.</span><span class="sxs-lookup"><span data-stu-id="ae34c-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="ae34c-141">Nastavení `requestQueueLimit` funguje stejným způsobem jako atribut `requestQueueLimit` prvku [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , který je nastaven v souborech Web. config pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ae34c-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="ae34c-142">Nastavení `requestQueueLimit` v souboru ASPNET. config však přepisuje nastavení `requestQueueLimit` v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="ae34c-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="ae34c-143">Jinými slovy, pokud jsou oba atributy nastaveny (ve výchozím nastavení je to pravda), má přednost nastavení `requestQueueLimit` v souboru ASPNET. config.</span><span class="sxs-lookup"><span data-stu-id="ae34c-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae34c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae34c-144">Example</span></span>  

<span data-ttu-id="ae34c-145">Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="ae34c-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="ae34c-146">Aplikace je hostována ve fondu aplikací služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="ae34c-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="ae34c-147">Služba IIS 7,0 je spuštěna v integrovaném režimu.</span><span class="sxs-lookup"><span data-stu-id="ae34c-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="ae34c-148">Aplikace používá .NET Framework 3,5 SP1 nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="ae34c-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="ae34c-149">Hodnoty v příkladu jsou výchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ae34c-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="ae34c-150">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="ae34c-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae34c-151">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ae34c-151">Namespace</span></span>||  
|<span data-ttu-id="ae34c-152">Název schématu</span><span class="sxs-lookup"><span data-stu-id="ae34c-152">Schema Name</span></span>||  
|<span data-ttu-id="ae34c-153">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="ae34c-153">Validation File</span></span>||  
|<span data-ttu-id="ae34c-154">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="ae34c-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="ae34c-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae34c-155">See also</span></span>

- [<span data-ttu-id="ae34c-156">@no__t element -1System. Web > (nastavení webu)</span><span class="sxs-lookup"><span data-stu-id="ae34c-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
