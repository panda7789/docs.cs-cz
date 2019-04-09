---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133819"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="bdf0b-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="bdf0b-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="bdf0b-104">Můžete použít tyto události nebo použití prostředků domény aplikace (ARM) funkci monitorování získávat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="bdf0b-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="bdf0b-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="bdf0b-106">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="bdf0b-107">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="bdf0b-108">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="bdf0b-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="bdf0b-109">ThreadAppDomainEnter Event</span><span class="sxs-lookup"><span data-stu-id="bdf0b-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="bdf0b-110">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="bdf0b-111">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="bdf0b-112">Tato událost se vyvolá také jako skrze zprostředkovatele doběhu `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="bdf0b-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="bdf0b-113">Toto je jediná událost, která je vyvolána v této kategorii skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="bdf0b-114">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="bdf0b-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="bdf0b-116">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-116">Keyword for raising the event</span></span>|<span data-ttu-id="bdf0b-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf0b-117">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="bdf0b-118">(0x800)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-118">(0x800)</span></span>|<span data-ttu-id="bdf0b-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-119">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="bdf0b-120">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-120">(0x10000)</span></span>|<span data-ttu-id="bdf0b-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="bdf0b-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bdf0b-123">Událost</span><span class="sxs-lookup"><span data-stu-id="bdf0b-123">Event</span></span>|<span data-ttu-id="bdf0b-124">ID události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-124">Event ID</span></span>|<span data-ttu-id="bdf0b-125">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="bdf0b-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="bdf0b-126">85</span><span class="sxs-lookup"><span data-stu-id="bdf0b-126">85</span></span>|<span data-ttu-id="bdf0b-127">Vlákno bylo vytvořeno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="bdf0b-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bdf0b-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="bdf0b-129">Field name</span></span>|<span data-ttu-id="bdf0b-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="bdf0b-130">Data type</span></span>|<span data-ttu-id="bdf0b-131">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf0b-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bdf0b-132">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="bdf0b-132">ThreadID</span></span>|<span data-ttu-id="bdf0b-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-133">win:UInt64</span></span>|<span data-ttu-id="bdf0b-134">ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="bdf0b-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-135">AppDomainID</span></span>|<span data-ttu-id="bdf0b-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-136">win:UInt64</span></span>|<span data-ttu-id="bdf0b-137">Identifikátor domény aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="bdf0b-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="bdf0b-138">Flags</span></span>|<span data-ttu-id="bdf0b-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bdf0b-139">win:UInt32</span></span>|<span data-ttu-id="bdf0b-140">Příznaky vytváření vlákna.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="bdf0b-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="bdf0b-141">ManagedThreadIndex</span></span>|<span data-ttu-id="bdf0b-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bdf0b-142">win:UInt32</span></span>|<span data-ttu-id="bdf0b-143">Spravovat indexu vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="bdf0b-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-144">OSThreadID</span></span>|<span data-ttu-id="bdf0b-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bdf0b-145">win:UInt32</span></span>|<span data-ttu-id="bdf0b-146">Operační systém ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="bdf0b-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-147">ClrInstanceID</span></span>|<span data-ttu-id="bdf0b-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bdf0b-148">win:UInt16</span></span>|<span data-ttu-id="bdf0b-149">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="bdf0b-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="bdf0b-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="bdf0b-151">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="bdf0b-152">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="bdf0b-153">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-153">Keyword for raising the event</span></span>|<span data-ttu-id="bdf0b-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf0b-154">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="bdf0b-155">(0x800)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-155">(0x800)</span></span>|<span data-ttu-id="bdf0b-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="bdf0b-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bdf0b-158">Událost</span><span class="sxs-lookup"><span data-stu-id="bdf0b-158">Event</span></span>|<span data-ttu-id="bdf0b-159">ID události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-159">Event ID</span></span>|<span data-ttu-id="bdf0b-160">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="bdf0b-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="bdf0b-161">83</span><span class="sxs-lookup"><span data-stu-id="bdf0b-161">83</span></span>|<span data-ttu-id="bdf0b-162">Každé 4 MB paměti (přibližně) je přidělena v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="bdf0b-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bdf0b-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="bdf0b-164">Field name</span></span>|<span data-ttu-id="bdf0b-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="bdf0b-165">Data type</span></span>|<span data-ttu-id="bdf0b-166">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf0b-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bdf0b-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-167">AppDomainID</span></span>|<span data-ttu-id="bdf0b-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-168">win:UInt64</span></span>|<span data-ttu-id="bdf0b-169">Identifikátor domény aplikace, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="bdf0b-170">přidělené</span><span class="sxs-lookup"><span data-stu-id="bdf0b-170">Allocated</span></span>|<span data-ttu-id="bdf0b-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-171">win:UInt64</span></span>|<span data-ttu-id="bdf0b-172">Celkový počet bajtů alokovaných v této doméně aplikace, od vytvoření domény aplikace (množství uvolněné paměti není odečtena).</span><span class="sxs-lookup"><span data-stu-id="bdf0b-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="bdf0b-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-173">ClrInstanceID</span></span>|<span data-ttu-id="bdf0b-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bdf0b-174">win:UInt16</span></span>|<span data-ttu-id="bdf0b-175">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="bdf0b-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="bdf0b-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="bdf0b-177">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="bdf0b-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="bdf0b-178">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="bdf0b-179">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-179">Keyword for raising the event</span></span>|<span data-ttu-id="bdf0b-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf0b-180">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="bdf0b-181">(0x800)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-181">(0x800)</span></span>|<span data-ttu-id="bdf0b-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="bdf0b-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bdf0b-184">Událost</span><span class="sxs-lookup"><span data-stu-id="bdf0b-184">Event</span></span>|<span data-ttu-id="bdf0b-185">ID události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-185">Event ID</span></span>|<span data-ttu-id="bdf0b-186">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="bdf0b-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="bdf0b-187">84</span><span class="sxs-lookup"><span data-stu-id="bdf0b-187">84</span></span>|<span data-ttu-id="bdf0b-188">Každá kolekce uvolnění paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="bdf0b-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bdf0b-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="bdf0b-190">Field name</span></span>|<span data-ttu-id="bdf0b-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="bdf0b-191">Data type</span></span>|<span data-ttu-id="bdf0b-192">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf0b-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bdf0b-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-193">AppDomainID</span></span>|<span data-ttu-id="bdf0b-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-194">win:UInt64</span></span>|<span data-ttu-id="bdf0b-195">Identifikátor domény, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="bdf0b-196">Zůstat naživu při</span><span class="sxs-lookup"><span data-stu-id="bdf0b-196">Survived</span></span>|<span data-ttu-id="bdf0b-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-197">win:UInt64</span></span>|<span data-ttu-id="bdf0b-198">Počet bajtů, které zůstat naživu po poslední a, které jsou známé uchovávat podle této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="bdf0b-199">Toto číslo je přesné a úplné po celé kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="bdf0b-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="bdf0b-200">ProcessSurvived</span></span>|<span data-ttu-id="bdf0b-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-201">win:UInt64</span></span>|<span data-ttu-id="bdf0b-202">Celkový počet bajtů, které zůstat naživu z posledního kolekce.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="bdf0b-203">Po celé kolekce toto číslo představuje počet bajtů se konají za provozu ve spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="bdf0b-204">Po dočasné kolekce toto číslo představuje počet bajtů uložených za provozu v dočasných generací.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="bdf0b-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-205">ClrInstanceID</span></span>|<span data-ttu-id="bdf0b-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bdf0b-206">win:UInt16</span></span>|<span data-ttu-id="bdf0b-207">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="bdf0b-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="bdf0b-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="bdf0b-209">ThreadAppDomainEnter Event</span><span class="sxs-lookup"><span data-stu-id="bdf0b-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="bdf0b-210">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="bdf0b-211">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-211">Keyword for raising the event</span></span>|<span data-ttu-id="bdf0b-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf0b-212">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="bdf0b-213">(0x800)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-213">(0x800)</span></span>|<span data-ttu-id="bdf0b-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-214">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="bdf0b-215">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-215">(0x10000)</span></span>|<span data-ttu-id="bdf0b-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="bdf0b-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bdf0b-218">Událost</span><span class="sxs-lookup"><span data-stu-id="bdf0b-218">Event</span></span>|<span data-ttu-id="bdf0b-219">ID události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-219">Event ID</span></span>|<span data-ttu-id="bdf0b-220">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="bdf0b-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="bdf0b-221">87</span><span class="sxs-lookup"><span data-stu-id="bdf0b-221">87</span></span>|<span data-ttu-id="bdf0b-222">Vlákno přejde do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="bdf0b-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bdf0b-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="bdf0b-224">Field name</span></span>|<span data-ttu-id="bdf0b-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="bdf0b-225">Data type</span></span>|<span data-ttu-id="bdf0b-226">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf0b-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bdf0b-227">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="bdf0b-227">ThreadID</span></span>|<span data-ttu-id="bdf0b-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-228">win:UInt64</span></span>|<span data-ttu-id="bdf0b-229">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-229">The thread identifier.</span></span>|  
|<span data-ttu-id="bdf0b-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-230">AppDomainID</span></span>|<span data-ttu-id="bdf0b-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-231">win:UInt64</span></span>|<span data-ttu-id="bdf0b-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="bdf0b-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-233">ClrInstanceID</span></span>|<span data-ttu-id="bdf0b-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bdf0b-234">win:UInt16</span></span>|<span data-ttu-id="bdf0b-235">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="bdf0b-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="bdf0b-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="bdf0b-237">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="bdf0b-238">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="bdf0b-239">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-239">Keyword for raising the event</span></span>|<span data-ttu-id="bdf0b-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf0b-240">Level</span></span>|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` <span data-ttu-id="bdf0b-241">(0x800)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-241">(0x800)</span></span>|<span data-ttu-id="bdf0b-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-242">Informational(4)</span></span>|  
|`ThreadingKeyword` <span data-ttu-id="bdf0b-243">(0x10000)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-243">(0x10000)</span></span>|<span data-ttu-id="bdf0b-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="bdf0b-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="bdf0b-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bdf0b-246">Událost</span><span class="sxs-lookup"><span data-stu-id="bdf0b-246">Event</span></span>|<span data-ttu-id="bdf0b-247">ID události</span><span class="sxs-lookup"><span data-stu-id="bdf0b-247">Event ID</span></span>|<span data-ttu-id="bdf0b-248">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="bdf0b-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="bdf0b-249">86</span><span class="sxs-lookup"><span data-stu-id="bdf0b-249">86</span></span>|<span data-ttu-id="bdf0b-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="bdf0b-251">V následující tabulce jsou uvedeny data události:</span><span class="sxs-lookup"><span data-stu-id="bdf0b-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="bdf0b-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="bdf0b-252">Field name</span></span>|<span data-ttu-id="bdf0b-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="bdf0b-253">Data type</span></span>|<span data-ttu-id="bdf0b-254">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf0b-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bdf0b-255">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="bdf0b-255">ThreadID</span></span>|<span data-ttu-id="bdf0b-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-256">win:UInt64</span></span>|<span data-ttu-id="bdf0b-257">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-257">The thread identifier.</span></span>|  
|<span data-ttu-id="bdf0b-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-258">AppDomainID</span></span>|<span data-ttu-id="bdf0b-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="bdf0b-259">win:UInt64</span></span>|<span data-ttu-id="bdf0b-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="bdf0b-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bdf0b-261">ClrInstanceID</span></span>|<span data-ttu-id="bdf0b-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bdf0b-262">win:UInt16</span></span>|<span data-ttu-id="bdf0b-263">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bdf0b-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdf0b-264">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdf0b-264">See also</span></span>

- [<span data-ttu-id="bdf0b-265">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="bdf0b-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
