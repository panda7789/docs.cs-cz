---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ac396e1a5b83f33068266553024c37ef436c150d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616637"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="19c69-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="19c69-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="19c69-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="19c69-104">Můžete použít tyto události nebo použití prostředků domény aplikace (ARM) funkci monitorování získávat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="19c69-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="19c69-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="19c69-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="19c69-106">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="19c69-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="19c69-107">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="19c69-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="19c69-108">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="19c69-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="19c69-109">ThreadAppDomainEnter události</span><span class="sxs-lookup"><span data-stu-id="19c69-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="19c69-110">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="19c69-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="19c69-111">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="19c69-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="19c69-112">Tato událost se vyvolá také jako skrze zprostředkovatele doběhu `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="19c69-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="19c69-113">Toto je jediná událost, která je vyvolána v této kategorii skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="19c69-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="19c69-114">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="19c69-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="19c69-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="19c69-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="19c69-116">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="19c69-116">Keyword for raising the event</span></span>|<span data-ttu-id="19c69-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="19c69-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="19c69-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="19c69-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="19c69-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-119">Informational(4)</span></span>|  
|<span data-ttu-id="19c69-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="19c69-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="19c69-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="19c69-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="19c69-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="19c69-123">Událost</span><span class="sxs-lookup"><span data-stu-id="19c69-123">Event</span></span>|<span data-ttu-id="19c69-124">ID události</span><span class="sxs-lookup"><span data-stu-id="19c69-124">Event ID</span></span>|<span data-ttu-id="19c69-125">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="19c69-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="19c69-126">85</span><span class="sxs-lookup"><span data-stu-id="19c69-126">85</span></span>|<span data-ttu-id="19c69-127">Vlákno bylo vytvořeno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="19c69-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="19c69-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="19c69-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="19c69-129">Field name</span></span>|<span data-ttu-id="19c69-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="19c69-130">Data type</span></span>|<span data-ttu-id="19c69-131">Popis</span><span class="sxs-lookup"><span data-stu-id="19c69-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="19c69-132">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="19c69-132">ThreadID</span></span>|<span data-ttu-id="19c69-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-133">win:UInt64</span></span>|<span data-ttu-id="19c69-134">ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="19c69-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="19c69-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="19c69-135">AppDomainID</span></span>|<span data-ttu-id="19c69-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-136">win:UInt64</span></span>|<span data-ttu-id="19c69-137">Identifikátor domény aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="19c69-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="19c69-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="19c69-138">Flags</span></span>|<span data-ttu-id="19c69-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="19c69-139">win:UInt32</span></span>|<span data-ttu-id="19c69-140">Příznaky vytváření vlákna.</span><span class="sxs-lookup"><span data-stu-id="19c69-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="19c69-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="19c69-141">ManagedThreadIndex</span></span>|<span data-ttu-id="19c69-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="19c69-142">win:UInt32</span></span>|<span data-ttu-id="19c69-143">Spravovat indexu vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="19c69-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="19c69-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="19c69-144">OSThreadID</span></span>|<span data-ttu-id="19c69-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="19c69-145">win:UInt32</span></span>|<span data-ttu-id="19c69-146">Operační systém ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="19c69-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="19c69-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19c69-147">ClrInstanceID</span></span>|<span data-ttu-id="19c69-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="19c69-148">win:UInt16</span></span>|<span data-ttu-id="19c69-149">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19c69-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="19c69-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="19c69-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="19c69-151">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="19c69-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="19c69-152">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="19c69-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="19c69-153">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="19c69-153">Keyword for raising the event</span></span>|<span data-ttu-id="19c69-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="19c69-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="19c69-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="19c69-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="19c69-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="19c69-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="19c69-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="19c69-158">Událost</span><span class="sxs-lookup"><span data-stu-id="19c69-158">Event</span></span>|<span data-ttu-id="19c69-159">ID události</span><span class="sxs-lookup"><span data-stu-id="19c69-159">Event ID</span></span>|<span data-ttu-id="19c69-160">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="19c69-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="19c69-161">83</span><span class="sxs-lookup"><span data-stu-id="19c69-161">83</span></span>|<span data-ttu-id="19c69-162">Každé 4 MB paměti (přibližně) je přidělena v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="19c69-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="19c69-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="19c69-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="19c69-164">Field name</span></span>|<span data-ttu-id="19c69-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="19c69-165">Data type</span></span>|<span data-ttu-id="19c69-166">Popis</span><span class="sxs-lookup"><span data-stu-id="19c69-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="19c69-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="19c69-167">AppDomainID</span></span>|<span data-ttu-id="19c69-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-168">win:UInt64</span></span>|<span data-ttu-id="19c69-169">Identifikátor domény aplikace, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="19c69-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="19c69-170">přidělené</span><span class="sxs-lookup"><span data-stu-id="19c69-170">Allocated</span></span>|<span data-ttu-id="19c69-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-171">win:UInt64</span></span>|<span data-ttu-id="19c69-172">Celkový počet bajtů alokovaných v této doméně aplikace, od vytvoření domény aplikace (množství uvolněné paměti není odečtena).</span><span class="sxs-lookup"><span data-stu-id="19c69-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="19c69-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19c69-173">ClrInstanceID</span></span>|<span data-ttu-id="19c69-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="19c69-174">win:UInt16</span></span>|<span data-ttu-id="19c69-175">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19c69-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="19c69-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="19c69-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="19c69-177">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="19c69-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="19c69-178">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="19c69-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="19c69-179">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="19c69-179">Keyword for raising the event</span></span>|<span data-ttu-id="19c69-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="19c69-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="19c69-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="19c69-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="19c69-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="19c69-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="19c69-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="19c69-184">Událost</span><span class="sxs-lookup"><span data-stu-id="19c69-184">Event</span></span>|<span data-ttu-id="19c69-185">ID události</span><span class="sxs-lookup"><span data-stu-id="19c69-185">Event ID</span></span>|<span data-ttu-id="19c69-186">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="19c69-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="19c69-187">84</span><span class="sxs-lookup"><span data-stu-id="19c69-187">84</span></span>|<span data-ttu-id="19c69-188">Každá kolekce uvolnění paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="19c69-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="19c69-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="19c69-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="19c69-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="19c69-190">Field name</span></span>|<span data-ttu-id="19c69-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="19c69-191">Data type</span></span>|<span data-ttu-id="19c69-192">Popis</span><span class="sxs-lookup"><span data-stu-id="19c69-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="19c69-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="19c69-193">AppDomainID</span></span>|<span data-ttu-id="19c69-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-194">win:UInt64</span></span>|<span data-ttu-id="19c69-195">Identifikátor domény, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="19c69-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="19c69-196">Zůstat naživu při</span><span class="sxs-lookup"><span data-stu-id="19c69-196">Survived</span></span>|<span data-ttu-id="19c69-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-197">win:UInt64</span></span>|<span data-ttu-id="19c69-198">Počet bajtů, které zůstat naživu po poslední a, které jsou známé uchovávat podle této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="19c69-199">Toto číslo je přesné a úplné po celé kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="19c69-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="19c69-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="19c69-200">ProcessSurvived</span></span>|<span data-ttu-id="19c69-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-201">win:UInt64</span></span>|<span data-ttu-id="19c69-202">Celkový počet bajtů, které zůstat naživu z posledního kolekce.</span><span class="sxs-lookup"><span data-stu-id="19c69-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="19c69-203">Po celé kolekce toto číslo představuje počet bajtů se konají za provozu ve spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="19c69-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="19c69-204">Po dočasné kolekce toto číslo představuje počet bajtů uložených za provozu v dočasných generací.</span><span class="sxs-lookup"><span data-stu-id="19c69-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="19c69-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19c69-205">ClrInstanceID</span></span>|<span data-ttu-id="19c69-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="19c69-206">win:UInt16</span></span>|<span data-ttu-id="19c69-207">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19c69-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="19c69-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="19c69-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="19c69-209">ThreadAppDomainEnter Event</span><span class="sxs-lookup"><span data-stu-id="19c69-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="19c69-210">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="19c69-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="19c69-211">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="19c69-211">Keyword for raising the event</span></span>|<span data-ttu-id="19c69-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="19c69-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="19c69-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="19c69-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="19c69-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-214">Informational(4)</span></span>|  
|<span data-ttu-id="19c69-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="19c69-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="19c69-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="19c69-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="19c69-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="19c69-218">Událost</span><span class="sxs-lookup"><span data-stu-id="19c69-218">Event</span></span>|<span data-ttu-id="19c69-219">ID události</span><span class="sxs-lookup"><span data-stu-id="19c69-219">Event ID</span></span>|<span data-ttu-id="19c69-220">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="19c69-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="19c69-221">87</span><span class="sxs-lookup"><span data-stu-id="19c69-221">87</span></span>|<span data-ttu-id="19c69-222">Vlákno přejde do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="19c69-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="19c69-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="19c69-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="19c69-224">Field name</span></span>|<span data-ttu-id="19c69-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="19c69-225">Data type</span></span>|<span data-ttu-id="19c69-226">Popis</span><span class="sxs-lookup"><span data-stu-id="19c69-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="19c69-227">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="19c69-227">ThreadID</span></span>|<span data-ttu-id="19c69-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-228">win:UInt64</span></span>|<span data-ttu-id="19c69-229">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="19c69-229">The thread identifier.</span></span>|  
|<span data-ttu-id="19c69-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="19c69-230">AppDomainID</span></span>|<span data-ttu-id="19c69-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-231">win:UInt64</span></span>|<span data-ttu-id="19c69-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="19c69-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19c69-233">ClrInstanceID</span></span>|<span data-ttu-id="19c69-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="19c69-234">win:UInt16</span></span>|<span data-ttu-id="19c69-235">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19c69-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="19c69-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="19c69-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="19c69-237">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="19c69-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="19c69-238">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="19c69-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="19c69-239">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="19c69-239">Keyword for raising the event</span></span>|<span data-ttu-id="19c69-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="19c69-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="19c69-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="19c69-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="19c69-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-242">Informational(4)</span></span>|  
|<span data-ttu-id="19c69-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="19c69-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="19c69-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="19c69-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="19c69-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="19c69-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="19c69-246">Událost</span><span class="sxs-lookup"><span data-stu-id="19c69-246">Event</span></span>|<span data-ttu-id="19c69-247">ID události</span><span class="sxs-lookup"><span data-stu-id="19c69-247">Event ID</span></span>|<span data-ttu-id="19c69-248">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="19c69-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="19c69-249">86</span><span class="sxs-lookup"><span data-stu-id="19c69-249">86</span></span>|<span data-ttu-id="19c69-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="19c69-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="19c69-251">V následující tabulce jsou uvedeny data události:</span><span class="sxs-lookup"><span data-stu-id="19c69-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="19c69-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="19c69-252">Field name</span></span>|<span data-ttu-id="19c69-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="19c69-253">Data type</span></span>|<span data-ttu-id="19c69-254">Popis</span><span class="sxs-lookup"><span data-stu-id="19c69-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="19c69-255">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="19c69-255">ThreadID</span></span>|<span data-ttu-id="19c69-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-256">win:UInt64</span></span>|<span data-ttu-id="19c69-257">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="19c69-257">The thread identifier.</span></span>|  
|<span data-ttu-id="19c69-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="19c69-258">AppDomainID</span></span>|<span data-ttu-id="19c69-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="19c69-259">win:UInt64</span></span>|<span data-ttu-id="19c69-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="19c69-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="19c69-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="19c69-261">ClrInstanceID</span></span>|<span data-ttu-id="19c69-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="19c69-262">win:UInt16</span></span>|<span data-ttu-id="19c69-263">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="19c69-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19c69-264">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19c69-264">See also</span></span>

- [<span data-ttu-id="19c69-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="19c69-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
