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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788060"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="3837e-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="3837e-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="3837e-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="3837e-104">Můžete použít tyto události nebo použití prostředků domény aplikace (ARM) funkci monitorování získávat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="3837e-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="3837e-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="3837e-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="3837e-106">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="3837e-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="3837e-107">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="3837e-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="3837e-108">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="3837e-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="3837e-109">ThreadAppDomainEnter události</span><span class="sxs-lookup"><span data-stu-id="3837e-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="3837e-110">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="3837e-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="3837e-111">ThreadCreated události</span><span class="sxs-lookup"><span data-stu-id="3837e-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="3837e-112">Tato událost se vyvolá také jako skrze zprostředkovatele doběhu `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="3837e-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="3837e-113">Toto je jediná událost, která je vyvolána v této kategorii skrze zprostředkovatele doběhu.</span><span class="sxs-lookup"><span data-stu-id="3837e-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="3837e-114">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="3837e-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="3837e-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="3837e-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="3837e-116">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="3837e-116">Keyword for raising the event</span></span>|<span data-ttu-id="3837e-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="3837e-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3837e-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="3837e-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="3837e-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-119">Informational(4)</span></span>|  
|<span data-ttu-id="3837e-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3837e-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3837e-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="3837e-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="3837e-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3837e-123">Událost</span><span class="sxs-lookup"><span data-stu-id="3837e-123">Event</span></span>|<span data-ttu-id="3837e-124">ID události</span><span class="sxs-lookup"><span data-stu-id="3837e-124">Event ID</span></span>|<span data-ttu-id="3837e-125">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="3837e-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="3837e-126">85</span><span class="sxs-lookup"><span data-stu-id="3837e-126">85</span></span>|<span data-ttu-id="3837e-127">Vlákno bylo vytvořeno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="3837e-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="3837e-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3837e-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="3837e-129">Field name</span></span>|<span data-ttu-id="3837e-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3837e-130">Data type</span></span>|<span data-ttu-id="3837e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="3837e-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3837e-132">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="3837e-132">ThreadID</span></span>|<span data-ttu-id="3837e-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-133">win:UInt64</span></span>|<span data-ttu-id="3837e-134">ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3837e-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="3837e-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="3837e-135">AppDomainID</span></span>|<span data-ttu-id="3837e-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-136">win:UInt64</span></span>|<span data-ttu-id="3837e-137">Identifikátor domény aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="3837e-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="3837e-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="3837e-138">Flags</span></span>|<span data-ttu-id="3837e-139">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3837e-139">win:UInt32</span></span>|<span data-ttu-id="3837e-140">Příznaky vytváření vlákna.</span><span class="sxs-lookup"><span data-stu-id="3837e-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="3837e-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="3837e-141">ManagedThreadIndex</span></span>|<span data-ttu-id="3837e-142">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3837e-142">win:UInt32</span></span>|<span data-ttu-id="3837e-143">Spravovat indexu vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3837e-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="3837e-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="3837e-144">OSThreadID</span></span>|<span data-ttu-id="3837e-145">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3837e-145">win:UInt32</span></span>|<span data-ttu-id="3837e-146">Operační systém ID vlákna, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="3837e-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="3837e-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3837e-147">ClrInstanceID</span></span>|<span data-ttu-id="3837e-148">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3837e-148">win:UInt16</span></span>|<span data-ttu-id="3837e-149">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3837e-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3837e-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3837e-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="3837e-151">AppDomainMemAllocated události</span><span class="sxs-lookup"><span data-stu-id="3837e-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="3837e-152">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="3837e-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3837e-153">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="3837e-153">Keyword for raising the event</span></span>|<span data-ttu-id="3837e-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="3837e-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3837e-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="3837e-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="3837e-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="3837e-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="3837e-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3837e-158">Událost</span><span class="sxs-lookup"><span data-stu-id="3837e-158">Event</span></span>|<span data-ttu-id="3837e-159">ID události</span><span class="sxs-lookup"><span data-stu-id="3837e-159">Event ID</span></span>|<span data-ttu-id="3837e-160">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="3837e-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="3837e-161">83</span><span class="sxs-lookup"><span data-stu-id="3837e-161">83</span></span>|<span data-ttu-id="3837e-162">Každé 4 MB paměti (přibližně) je přidělena v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="3837e-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="3837e-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3837e-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="3837e-164">Field name</span></span>|<span data-ttu-id="3837e-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3837e-165">Data type</span></span>|<span data-ttu-id="3837e-166">Popis</span><span class="sxs-lookup"><span data-stu-id="3837e-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3837e-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="3837e-167">AppDomainID</span></span>|<span data-ttu-id="3837e-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-168">win:UInt64</span></span>|<span data-ttu-id="3837e-169">Identifikátor domény aplikace, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="3837e-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="3837e-170">přidělené</span><span class="sxs-lookup"><span data-stu-id="3837e-170">Allocated</span></span>|<span data-ttu-id="3837e-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-171">win:UInt64</span></span>|<span data-ttu-id="3837e-172">Celkový počet bajtů alokovaných v této doméně aplikace, od vytvoření domény aplikace (množství uvolněné paměti není odečtena).</span><span class="sxs-lookup"><span data-stu-id="3837e-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="3837e-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3837e-173">ClrInstanceID</span></span>|<span data-ttu-id="3837e-174">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3837e-174">win:UInt16</span></span>|<span data-ttu-id="3837e-175">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3837e-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3837e-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3837e-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="3837e-177">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="3837e-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="3837e-178">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="3837e-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3837e-179">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="3837e-179">Keyword for raising the event</span></span>|<span data-ttu-id="3837e-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="3837e-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3837e-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="3837e-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="3837e-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="3837e-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="3837e-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3837e-184">Událost</span><span class="sxs-lookup"><span data-stu-id="3837e-184">Event</span></span>|<span data-ttu-id="3837e-185">ID události</span><span class="sxs-lookup"><span data-stu-id="3837e-185">Event ID</span></span>|<span data-ttu-id="3837e-186">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="3837e-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="3837e-187">84</span><span class="sxs-lookup"><span data-stu-id="3837e-187">84</span></span>|<span data-ttu-id="3837e-188">Každá kolekce uvolnění paměti bylo již ukončeno.</span><span class="sxs-lookup"><span data-stu-id="3837e-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="3837e-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="3837e-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3837e-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="3837e-190">Field name</span></span>|<span data-ttu-id="3837e-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3837e-191">Data type</span></span>|<span data-ttu-id="3837e-192">Popis</span><span class="sxs-lookup"><span data-stu-id="3837e-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3837e-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="3837e-193">AppDomainID</span></span>|<span data-ttu-id="3837e-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-194">win:UInt64</span></span>|<span data-ttu-id="3837e-195">Identifikátor domény, pro který prostředek se hlásí využití.</span><span class="sxs-lookup"><span data-stu-id="3837e-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="3837e-196">Zůstat naživu při</span><span class="sxs-lookup"><span data-stu-id="3837e-196">Survived</span></span>|<span data-ttu-id="3837e-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-197">win:UInt64</span></span>|<span data-ttu-id="3837e-198">Počet bajtů, které zůstat naživu po poslední a, které jsou známé uchovávat podle této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="3837e-199">Toto číslo je přesné a úplné po celé kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="3837e-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="3837e-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="3837e-200">ProcessSurvived</span></span>|<span data-ttu-id="3837e-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-201">win:UInt64</span></span>|<span data-ttu-id="3837e-202">Celkový počet bajtů, které zůstat naživu z posledního kolekce.</span><span class="sxs-lookup"><span data-stu-id="3837e-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="3837e-203">Po celé kolekce toto číslo představuje počet bajtů se konají za provozu ve spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="3837e-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="3837e-204">Po dočasné kolekce toto číslo představuje počet bajtů uložených za provozu v dočasných generací.</span><span class="sxs-lookup"><span data-stu-id="3837e-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="3837e-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3837e-205">ClrInstanceID</span></span>|<span data-ttu-id="3837e-206">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3837e-206">win:UInt16</span></span>|<span data-ttu-id="3837e-207">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3837e-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3837e-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3837e-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="3837e-209">ThreadAppDomainEnter Event</span><span class="sxs-lookup"><span data-stu-id="3837e-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="3837e-210">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="3837e-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3837e-211">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="3837e-211">Keyword for raising the event</span></span>|<span data-ttu-id="3837e-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="3837e-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3837e-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="3837e-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="3837e-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-214">Informational(4)</span></span>|  
|<span data-ttu-id="3837e-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3837e-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3837e-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="3837e-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="3837e-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3837e-218">Událost</span><span class="sxs-lookup"><span data-stu-id="3837e-218">Event</span></span>|<span data-ttu-id="3837e-219">ID události</span><span class="sxs-lookup"><span data-stu-id="3837e-219">Event ID</span></span>|<span data-ttu-id="3837e-220">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="3837e-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="3837e-221">87</span><span class="sxs-lookup"><span data-stu-id="3837e-221">87</span></span>|<span data-ttu-id="3837e-222">Vlákno přejde do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="3837e-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="3837e-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="3837e-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="3837e-224">Field name</span></span>|<span data-ttu-id="3837e-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3837e-225">Data type</span></span>|<span data-ttu-id="3837e-226">Popis</span><span class="sxs-lookup"><span data-stu-id="3837e-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3837e-227">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="3837e-227">ThreadID</span></span>|<span data-ttu-id="3837e-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-228">win:UInt64</span></span>|<span data-ttu-id="3837e-229">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="3837e-229">The thread identifier.</span></span>|  
|<span data-ttu-id="3837e-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="3837e-230">AppDomainID</span></span>|<span data-ttu-id="3837e-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-231">win:UInt64</span></span>|<span data-ttu-id="3837e-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="3837e-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3837e-233">ClrInstanceID</span></span>|<span data-ttu-id="3837e-234">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3837e-234">win:UInt16</span></span>|<span data-ttu-id="3837e-235">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3837e-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="3837e-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="3837e-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="3837e-237">ThreadTerminated události</span><span class="sxs-lookup"><span data-stu-id="3837e-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="3837e-238">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="3837e-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="3837e-239">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="3837e-239">Keyword for raising the event</span></span>|<span data-ttu-id="3837e-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="3837e-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3837e-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="3837e-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="3837e-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-242">Informational(4)</span></span>|  
|<span data-ttu-id="3837e-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3837e-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3837e-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="3837e-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="3837e-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="3837e-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="3837e-246">Událost</span><span class="sxs-lookup"><span data-stu-id="3837e-246">Event</span></span>|<span data-ttu-id="3837e-247">ID události</span><span class="sxs-lookup"><span data-stu-id="3837e-247">Event ID</span></span>|<span data-ttu-id="3837e-248">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="3837e-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="3837e-249">86</span><span class="sxs-lookup"><span data-stu-id="3837e-249">86</span></span>|<span data-ttu-id="3837e-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="3837e-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="3837e-251">V následující tabulce jsou uvedeny data události:</span><span class="sxs-lookup"><span data-stu-id="3837e-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="3837e-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="3837e-252">Field name</span></span>|<span data-ttu-id="3837e-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3837e-253">Data type</span></span>|<span data-ttu-id="3837e-254">Popis</span><span class="sxs-lookup"><span data-stu-id="3837e-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3837e-255">Idvlákna</span><span class="sxs-lookup"><span data-stu-id="3837e-255">ThreadID</span></span>|<span data-ttu-id="3837e-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-256">win:UInt64</span></span>|<span data-ttu-id="3837e-257">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="3837e-257">The thread identifier.</span></span>|  
|<span data-ttu-id="3837e-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="3837e-258">AppDomainID</span></span>|<span data-ttu-id="3837e-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="3837e-259">win:UInt64</span></span>|<span data-ttu-id="3837e-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3837e-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="3837e-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3837e-261">ClrInstanceID</span></span>|<span data-ttu-id="3837e-262">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3837e-262">win:UInt16</span></span>|<span data-ttu-id="3837e-263">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="3837e-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3837e-264">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3837e-264">See also</span></span>

- [<span data-ttu-id="3837e-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="3837e-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
