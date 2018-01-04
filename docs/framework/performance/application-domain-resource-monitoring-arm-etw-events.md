---
title: "Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6384700c7039cb705f2db759ebd3d733bf8954ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="fcdb6-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="fcdb6-103">Tyto události poskytují podrobné diagnostické informace týkající se stavu služby domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="fcdb6-104">Můžete použít tyto události nebo pomocí prostředků domény aplikace (ARM) funkci monitorování získat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="fcdb6-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="fcdb6-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="fcdb6-106">Threadcreated – událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="fcdb6-107">AppDomainMemAllocated událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="fcdb6-108">AppDomainMemSurvived událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="fcdb6-109">ThreadAppDomainEnter událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="fcdb6-110">ThreadTerminated událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="fcdb6-111">Threadcreated – událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="fcdb6-112">Tato událost je aktivována také v rámci sekvence daneho zprostředkovatele jako `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="fcdb6-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="fcdb6-113">Toto je pouze událost, která se vyvolá v rámci sekvence daneho zprostředkovatele v této kategorii.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="fcdb6-114">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="fcdb6-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="fcdb6-116">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-116">Keyword for raising the event</span></span>|<span data-ttu-id="fcdb6-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="fcdb6-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fcdb6-118">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fcdb6-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-119">Informational(4)</span></span>|  
|<span data-ttu-id="fcdb6-120">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fcdb6-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="fcdb6-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fcdb6-123">Událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-123">Event</span></span>|<span data-ttu-id="fcdb6-124">ID události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-124">Event ID</span></span>|<span data-ttu-id="fcdb6-125">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fcdb6-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="fcdb6-126">85</span><span class="sxs-lookup"><span data-stu-id="fcdb6-126">85</span></span>|<span data-ttu-id="fcdb6-127">Vlákno byl vytvořen pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="fcdb6-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fcdb6-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="fcdb6-129">Field name</span></span>|<span data-ttu-id="fcdb6-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fcdb6-130">Data type</span></span>|<span data-ttu-id="fcdb6-131">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb6-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fcdb6-132">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="fcdb6-132">ThreadID</span></span>|<span data-ttu-id="fcdb6-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-133">win:UInt64</span></span>|<span data-ttu-id="fcdb6-134">ID vlákna, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="fcdb6-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-135">AppDomainID</span></span>|<span data-ttu-id="fcdb6-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-136">win:UInt64</span></span>|<span data-ttu-id="fcdb6-137">Identifikátor doménu aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="fcdb6-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="fcdb6-138">Flags</span></span>|<span data-ttu-id="fcdb6-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fcdb6-139">win:UInt32</span></span>|<span data-ttu-id="fcdb6-140">Vytvoření příznaky přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="fcdb6-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="fcdb6-141">ManagedThreadIndex</span></span>|<span data-ttu-id="fcdb6-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fcdb6-142">win:UInt32</span></span>|<span data-ttu-id="fcdb6-143">Spravované index vláken, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="fcdb6-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-144">OSThreadID</span></span>|<span data-ttu-id="fcdb6-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fcdb6-145">win:UInt32</span></span>|<span data-ttu-id="fcdb6-146">Operační systém ID vlákna, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="fcdb6-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-147">ClrInstanceID</span></span>|<span data-ttu-id="fcdb6-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fcdb6-148">win:UInt16</span></span>|<span data-ttu-id="fcdb6-149">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fcdb6-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fcdb6-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="fcdb6-151">AppDomainMemAllocated událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="fcdb6-152">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fcdb6-153">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-153">Keyword for raising the event</span></span>|<span data-ttu-id="fcdb6-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="fcdb6-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fcdb6-155">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fcdb6-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="fcdb6-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fcdb6-158">Událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-158">Event</span></span>|<span data-ttu-id="fcdb6-159">ID události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-159">Event ID</span></span>|<span data-ttu-id="fcdb6-160">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fcdb6-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="fcdb6-161">83</span><span class="sxs-lookup"><span data-stu-id="fcdb6-161">83</span></span>|<span data-ttu-id="fcdb6-162">Každý 4 MB paměti (přibližně) je přidělen v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="fcdb6-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fcdb6-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="fcdb6-164">Field name</span></span>|<span data-ttu-id="fcdb6-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fcdb6-165">Data type</span></span>|<span data-ttu-id="fcdb6-166">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb6-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fcdb6-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-167">AppDomainID</span></span>|<span data-ttu-id="fcdb6-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-168">win:UInt64</span></span>|<span data-ttu-id="fcdb6-169">Identifikátor doménu aplikace, pro který prostředek je hlášena využití.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="fcdb6-170">Přidělené</span><span class="sxs-lookup"><span data-stu-id="fcdb6-170">Allocated</span></span>|<span data-ttu-id="fcdb6-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-171">win:UInt64</span></span>|<span data-ttu-id="fcdb6-172">Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečítat).</span><span class="sxs-lookup"><span data-stu-id="fcdb6-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="fcdb6-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-173">ClrInstanceID</span></span>|<span data-ttu-id="fcdb6-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fcdb6-174">win:UInt16</span></span>|<span data-ttu-id="fcdb6-175">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fcdb6-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fcdb6-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="fcdb6-177">AppDomainMemSurvived událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="fcdb6-178">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fcdb6-179">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-179">Keyword for raising the event</span></span>|<span data-ttu-id="fcdb6-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="fcdb6-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fcdb6-181">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fcdb6-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="fcdb6-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fcdb6-184">Událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-184">Event</span></span>|<span data-ttu-id="fcdb6-185">ID události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-185">Event ID</span></span>|<span data-ttu-id="fcdb6-186">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fcdb6-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="fcdb6-187">84</span><span class="sxs-lookup"><span data-stu-id="fcdb6-187">84</span></span>|<span data-ttu-id="fcdb6-188">Uvolňování paměti jednotlivých byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="fcdb6-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fcdb6-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="fcdb6-190">Field name</span></span>|<span data-ttu-id="fcdb6-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fcdb6-191">Data type</span></span>|<span data-ttu-id="fcdb6-192">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb6-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fcdb6-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-193">AppDomainID</span></span>|<span data-ttu-id="fcdb6-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-194">win:UInt64</span></span>|<span data-ttu-id="fcdb6-195">Identifikátor domény, pro který prostředek je hlášena využití.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="fcdb6-196">Zůstal naživu</span><span class="sxs-lookup"><span data-stu-id="fcdb6-196">Survived</span></span>|<span data-ttu-id="fcdb6-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-197">win:UInt64</span></span>|<span data-ttu-id="fcdb6-198">Počet bajtů, který zůstal naživu po poslední kolekce a které jsou známé uchovávat tato doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="fcdb6-199">Toto číslo je přesné a úplné po úplné kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="fcdb6-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="fcdb6-200">ProcessSurvived</span></span>|<span data-ttu-id="fcdb6-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-201">win:UInt64</span></span>|<span data-ttu-id="fcdb6-202">Celkový počet bajtů, které zůstal naživu z poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="fcdb6-203">Po kompletní sadu toto číslo představuje počet bajtů, se uchovávat za provozu ve spravovaných haldách.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="fcdb6-204">Po dočasné kolekce toto číslo představuje počet bajtů uchovávat v dočasných generace za provozu.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="fcdb6-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-205">ClrInstanceID</span></span>|<span data-ttu-id="fcdb6-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fcdb6-206">win:UInt16</span></span>|<span data-ttu-id="fcdb6-207">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fcdb6-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fcdb6-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="fcdb6-209">ThreadAppDomainEnter událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="fcdb6-210">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fcdb6-211">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-211">Keyword for raising the event</span></span>|<span data-ttu-id="fcdb6-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="fcdb6-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fcdb6-213">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fcdb6-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-214">Informational(4)</span></span>|  
|<span data-ttu-id="fcdb6-215">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fcdb6-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="fcdb6-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fcdb6-218">Událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-218">Event</span></span>|<span data-ttu-id="fcdb6-219">ID události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-219">Event ID</span></span>|<span data-ttu-id="fcdb6-220">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fcdb6-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="fcdb6-221">87</span><span class="sxs-lookup"><span data-stu-id="fcdb6-221">87</span></span>|<span data-ttu-id="fcdb6-222">Vlákno vstupuje do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="fcdb6-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fcdb6-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="fcdb6-224">Field name</span></span>|<span data-ttu-id="fcdb6-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fcdb6-225">Data type</span></span>|<span data-ttu-id="fcdb6-226">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb6-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fcdb6-227">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="fcdb6-227">ThreadID</span></span>|<span data-ttu-id="fcdb6-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-228">win:UInt64</span></span>|<span data-ttu-id="fcdb6-229">Identifikátor přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-229">The thread identifier.</span></span>|  
|<span data-ttu-id="fcdb6-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-230">AppDomainID</span></span>|<span data-ttu-id="fcdb6-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-231">win:UInt64</span></span>|<span data-ttu-id="fcdb6-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="fcdb6-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-233">ClrInstanceID</span></span>|<span data-ttu-id="fcdb6-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fcdb6-234">win:UInt16</span></span>|<span data-ttu-id="fcdb6-235">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fcdb6-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="fcdb6-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="fcdb6-237">ThreadTerminated událostí</span><span class="sxs-lookup"><span data-stu-id="fcdb6-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="fcdb6-238">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fcdb6-239">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-239">Keyword for raising the event</span></span>|<span data-ttu-id="fcdb6-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="fcdb6-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fcdb6-241">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="fcdb6-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-242">Informational(4)</span></span>|  
|<span data-ttu-id="fcdb6-243">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="fcdb6-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fcdb6-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="fcdb6-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fcdb6-246">Událost</span><span class="sxs-lookup"><span data-stu-id="fcdb6-246">Event</span></span>|<span data-ttu-id="fcdb6-247">ID události</span><span class="sxs-lookup"><span data-stu-id="fcdb6-247">Event ID</span></span>|<span data-ttu-id="fcdb6-248">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="fcdb6-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="fcdb6-249">86</span><span class="sxs-lookup"><span data-stu-id="fcdb6-249">86</span></span>|<span data-ttu-id="fcdb6-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="fcdb6-251">Následující tabulka zobrazuje data událostí:</span><span class="sxs-lookup"><span data-stu-id="fcdb6-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="fcdb6-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="fcdb6-252">Field name</span></span>|<span data-ttu-id="fcdb6-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="fcdb6-253">Data type</span></span>|<span data-ttu-id="fcdb6-254">Popis</span><span class="sxs-lookup"><span data-stu-id="fcdb6-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fcdb6-255">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="fcdb6-255">ThreadID</span></span>|<span data-ttu-id="fcdb6-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-256">win:UInt64</span></span>|<span data-ttu-id="fcdb6-257">Identifikátor přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-257">The thread identifier.</span></span>|  
|<span data-ttu-id="fcdb6-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-258">AppDomainID</span></span>|<span data-ttu-id="fcdb6-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="fcdb6-259">win:UInt64</span></span>|<span data-ttu-id="fcdb6-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="fcdb6-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fcdb6-261">ClrInstanceID</span></span>|<span data-ttu-id="fcdb6-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fcdb6-262">win:UInt16</span></span>|<span data-ttu-id="fcdb6-263">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="fcdb6-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcdb6-264">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcdb6-264">See Also</span></span>  
 [<span data-ttu-id="fcdb6-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="fcdb6-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
