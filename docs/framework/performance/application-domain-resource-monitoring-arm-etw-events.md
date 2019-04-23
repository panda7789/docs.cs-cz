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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133819"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="46631-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="46631-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="46631-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="46631-104">Můžete použít tyto události nebo použití prostředků domény aplikace (ARM) funkci monitorování získávat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="46631-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="46631-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="46631-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="46631-106">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="46631-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="46631-107">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="46631-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="46631-108">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="46631-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="46631-109">ThreadAppDomainEnter události</span><span class="sxs-lookup"><span data-stu-id="46631-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="46631-110">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="46631-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="46631-111">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="46631-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="46631-112">Tato událost se vyvolá také jako skrze zprostředkovatele doběhu `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="46631-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="46631-113">Toto je jediná událost, která je vyvolána v této kategorii skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="46631-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="46631-114">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="46631-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="46631-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="46631-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="46631-116">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="46631-116">Keyword for raising the event</span></span>|<span data-ttu-id="46631-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="46631-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="46631-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="46631-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="46631-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-119">Informational(4)</span></span>|  
|<span data-ttu-id="46631-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="46631-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="46631-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="46631-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="46631-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="46631-123">Událost</span><span class="sxs-lookup"><span data-stu-id="46631-123">Event</span></span>|<span data-ttu-id="46631-124">ID události</span><span class="sxs-lookup"><span data-stu-id="46631-124">Event ID</span></span>|<span data-ttu-id="46631-125">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="46631-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="46631-126">85</span><span class="sxs-lookup"><span data-stu-id="46631-126">85</span></span>|<span data-ttu-id="46631-127">Vlákno bylo vytvořeno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="46631-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="46631-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="46631-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="46631-129">Field name</span></span>|<span data-ttu-id="46631-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="46631-130">Data type</span></span>|<span data-ttu-id="46631-131">Popis</span><span class="sxs-lookup"><span data-stu-id="46631-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="46631-132">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="46631-132">ThreadID</span></span>|<span data-ttu-id="46631-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-133">win:UInt64</span></span>|<span data-ttu-id="46631-134">ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="46631-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="46631-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="46631-135">AppDomainID</span></span>|<span data-ttu-id="46631-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-136">win:UInt64</span></span>|<span data-ttu-id="46631-137">Identifikátor domény aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="46631-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="46631-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="46631-138">Flags</span></span>|<span data-ttu-id="46631-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="46631-139">win:UInt32</span></span>|<span data-ttu-id="46631-140">Příznaky vytváření vlákna.</span><span class="sxs-lookup"><span data-stu-id="46631-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="46631-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="46631-141">ManagedThreadIndex</span></span>|<span data-ttu-id="46631-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="46631-142">win:UInt32</span></span>|<span data-ttu-id="46631-143">Spravovat indexu vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="46631-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="46631-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="46631-144">OSThreadID</span></span>|<span data-ttu-id="46631-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="46631-145">win:UInt32</span></span>|<span data-ttu-id="46631-146">Operační systém ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="46631-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="46631-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="46631-147">ClrInstanceID</span></span>|<span data-ttu-id="46631-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="46631-148">win:UInt16</span></span>|<span data-ttu-id="46631-149">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="46631-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="46631-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="46631-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="46631-151">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="46631-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="46631-152">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="46631-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="46631-153">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="46631-153">Keyword for raising the event</span></span>|<span data-ttu-id="46631-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="46631-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="46631-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="46631-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="46631-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="46631-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="46631-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="46631-158">Událost</span><span class="sxs-lookup"><span data-stu-id="46631-158">Event</span></span>|<span data-ttu-id="46631-159">ID události</span><span class="sxs-lookup"><span data-stu-id="46631-159">Event ID</span></span>|<span data-ttu-id="46631-160">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="46631-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="46631-161">83</span><span class="sxs-lookup"><span data-stu-id="46631-161">83</span></span>|<span data-ttu-id="46631-162">Každé 4 MB paměti (přibližně) je přidělena v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="46631-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="46631-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="46631-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="46631-164">Field name</span></span>|<span data-ttu-id="46631-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="46631-165">Data type</span></span>|<span data-ttu-id="46631-166">Popis</span><span class="sxs-lookup"><span data-stu-id="46631-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="46631-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="46631-167">AppDomainID</span></span>|<span data-ttu-id="46631-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-168">win:UInt64</span></span>|<span data-ttu-id="46631-169">Identifikátor domény aplikace, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="46631-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="46631-170">přidělené</span><span class="sxs-lookup"><span data-stu-id="46631-170">Allocated</span></span>|<span data-ttu-id="46631-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-171">win:UInt64</span></span>|<span data-ttu-id="46631-172">Celkový počet bajtů alokovaných v této doméně aplikace, od vytvoření domény aplikace (množství uvolněné paměti není odečtena).</span><span class="sxs-lookup"><span data-stu-id="46631-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="46631-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="46631-173">ClrInstanceID</span></span>|<span data-ttu-id="46631-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="46631-174">win:UInt16</span></span>|<span data-ttu-id="46631-175">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="46631-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="46631-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="46631-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="46631-177">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="46631-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="46631-178">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="46631-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="46631-179">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="46631-179">Keyword for raising the event</span></span>|<span data-ttu-id="46631-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="46631-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="46631-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="46631-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="46631-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="46631-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="46631-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="46631-184">Událost</span><span class="sxs-lookup"><span data-stu-id="46631-184">Event</span></span>|<span data-ttu-id="46631-185">ID události</span><span class="sxs-lookup"><span data-stu-id="46631-185">Event ID</span></span>|<span data-ttu-id="46631-186">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="46631-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="46631-187">84</span><span class="sxs-lookup"><span data-stu-id="46631-187">84</span></span>|<span data-ttu-id="46631-188">Každá kolekce uvolnění paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="46631-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="46631-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="46631-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="46631-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="46631-190">Field name</span></span>|<span data-ttu-id="46631-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="46631-191">Data type</span></span>|<span data-ttu-id="46631-192">Popis</span><span class="sxs-lookup"><span data-stu-id="46631-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="46631-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="46631-193">AppDomainID</span></span>|<span data-ttu-id="46631-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-194">win:UInt64</span></span>|<span data-ttu-id="46631-195">Identifikátor domény, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="46631-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="46631-196">Zůstat naživu při</span><span class="sxs-lookup"><span data-stu-id="46631-196">Survived</span></span>|<span data-ttu-id="46631-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-197">win:UInt64</span></span>|<span data-ttu-id="46631-198">Počet bajtů, které zůstat naživu po poslední a, které jsou známé uchovávat podle této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="46631-199">Toto číslo je přesné a úplné po celé kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="46631-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="46631-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="46631-200">ProcessSurvived</span></span>|<span data-ttu-id="46631-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-201">win:UInt64</span></span>|<span data-ttu-id="46631-202">Celkový počet bajtů, které zůstat naživu z posledního kolekce.</span><span class="sxs-lookup"><span data-stu-id="46631-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="46631-203">Po celé kolekce toto číslo představuje počet bajtů se konají za provozu ve spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="46631-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="46631-204">Po dočasné kolekce toto číslo představuje počet bajtů uložených za provozu v dočasných generací.</span><span class="sxs-lookup"><span data-stu-id="46631-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="46631-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="46631-205">ClrInstanceID</span></span>|<span data-ttu-id="46631-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="46631-206">win:UInt16</span></span>|<span data-ttu-id="46631-207">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="46631-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="46631-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="46631-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="46631-209">ThreadAppDomainEnter Event</span><span class="sxs-lookup"><span data-stu-id="46631-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="46631-210">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="46631-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="46631-211">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="46631-211">Keyword for raising the event</span></span>|<span data-ttu-id="46631-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="46631-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="46631-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="46631-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="46631-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-214">Informational(4)</span></span>|  
|<span data-ttu-id="46631-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="46631-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="46631-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="46631-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="46631-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="46631-218">Událost</span><span class="sxs-lookup"><span data-stu-id="46631-218">Event</span></span>|<span data-ttu-id="46631-219">ID události</span><span class="sxs-lookup"><span data-stu-id="46631-219">Event ID</span></span>|<span data-ttu-id="46631-220">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="46631-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="46631-221">87</span><span class="sxs-lookup"><span data-stu-id="46631-221">87</span></span>|<span data-ttu-id="46631-222">Vlákno přejde do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="46631-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="46631-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="46631-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="46631-224">Field name</span></span>|<span data-ttu-id="46631-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="46631-225">Data type</span></span>|<span data-ttu-id="46631-226">Popis</span><span class="sxs-lookup"><span data-stu-id="46631-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="46631-227">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="46631-227">ThreadID</span></span>|<span data-ttu-id="46631-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-228">win:UInt64</span></span>|<span data-ttu-id="46631-229">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="46631-229">The thread identifier.</span></span>|  
|<span data-ttu-id="46631-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="46631-230">AppDomainID</span></span>|<span data-ttu-id="46631-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-231">win:UInt64</span></span>|<span data-ttu-id="46631-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="46631-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="46631-233">ClrInstanceID</span></span>|<span data-ttu-id="46631-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="46631-234">win:UInt16</span></span>|<span data-ttu-id="46631-235">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="46631-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="46631-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="46631-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="46631-237">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="46631-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="46631-238">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="46631-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="46631-239">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="46631-239">Keyword for raising the event</span></span>|<span data-ttu-id="46631-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="46631-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="46631-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="46631-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="46631-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-242">Informational(4)</span></span>|  
|<span data-ttu-id="46631-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="46631-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="46631-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="46631-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="46631-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="46631-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="46631-246">Událost</span><span class="sxs-lookup"><span data-stu-id="46631-246">Event</span></span>|<span data-ttu-id="46631-247">ID události</span><span class="sxs-lookup"><span data-stu-id="46631-247">Event ID</span></span>|<span data-ttu-id="46631-248">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="46631-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="46631-249">86</span><span class="sxs-lookup"><span data-stu-id="46631-249">86</span></span>|<span data-ttu-id="46631-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="46631-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="46631-251">V následující tabulce jsou uvedeny data události:</span><span class="sxs-lookup"><span data-stu-id="46631-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="46631-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="46631-252">Field name</span></span>|<span data-ttu-id="46631-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="46631-253">Data type</span></span>|<span data-ttu-id="46631-254">Popis</span><span class="sxs-lookup"><span data-stu-id="46631-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="46631-255">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="46631-255">ThreadID</span></span>|<span data-ttu-id="46631-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-256">win:UInt64</span></span>|<span data-ttu-id="46631-257">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="46631-257">The thread identifier.</span></span>|  
|<span data-ttu-id="46631-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="46631-258">AppDomainID</span></span>|<span data-ttu-id="46631-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="46631-259">win:UInt64</span></span>|<span data-ttu-id="46631-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="46631-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="46631-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="46631-261">ClrInstanceID</span></span>|<span data-ttu-id="46631-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="46631-262">win:UInt16</span></span>|<span data-ttu-id="46631-263">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="46631-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46631-264">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46631-264">See also</span></span>

- [<span data-ttu-id="46631-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="46631-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
