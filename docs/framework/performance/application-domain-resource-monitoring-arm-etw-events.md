---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046773"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="ae0d9-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a><span data-ttu-id="ae0d9-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="ae0d9-104">Tyto události můžete použít, nebo můžete použít funkci monitorování prostředků domény aplikace (ARM) a získat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="ae0d9-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="ae0d9-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="ae0d9-106">Událost ThreadCreated –</span><span class="sxs-lookup"><span data-stu-id="ae0d9-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
- [<span data-ttu-id="ae0d9-107">Událost AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="ae0d9-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
- [<span data-ttu-id="ae0d9-108">AppDomainMemSurvived Event</span><span class="sxs-lookup"><span data-stu-id="ae0d9-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
- [<span data-ttu-id="ae0d9-109">Událost ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="ae0d9-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
- [<span data-ttu-id="ae0d9-110">Událost ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="ae0d9-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="ae0d9-111">Událost ThreadCreated –</span><span class="sxs-lookup"><span data-stu-id="ae0d9-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="ae0d9-112">Tato událost se taky vyvolala pod poskytovatelem `ThreadDC` doběhu jako ( `AppDomainResourceManagementRundownKeyword` pod klíčovým slovem).</span><span class="sxs-lookup"><span data-stu-id="ae0d9-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="ae0d9-113">Toto je jediná událost, která je vyvolána v rámci poskytovatele doběhu v této kategorii.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="ae0d9-114">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="ae0d9-115">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ae0d9-116">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-116">Keyword for raising the event</span></span>|<span data-ttu-id="ae0d9-117">Level</span><span class="sxs-lookup"><span data-stu-id="ae0d9-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae0d9-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ae0d9-119">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-119">Informational(4)</span></span>|  
|<span data-ttu-id="ae0d9-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ae0d9-121">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="ae0d9-122">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae0d9-123">Událost</span><span class="sxs-lookup"><span data-stu-id="ae0d9-123">Event</span></span>|<span data-ttu-id="ae0d9-124">ID události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-124">Event ID</span></span>|<span data-ttu-id="ae0d9-125">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ae0d9-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="ae0d9-126">85</span><span class="sxs-lookup"><span data-stu-id="ae0d9-126">85</span></span>|<span data-ttu-id="ae0d9-127">Bylo vytvořeno vlákno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="ae0d9-128">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae0d9-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="ae0d9-129">Field name</span></span>|<span data-ttu-id="ae0d9-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ae0d9-130">Data type</span></span>|<span data-ttu-id="ae0d9-131">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0d9-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae0d9-132">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="ae0d9-132">ThreadID</span></span>|<span data-ttu-id="ae0d9-133">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-133">win:UInt64</span></span>|<span data-ttu-id="ae0d9-134">ID vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="ae0d9-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-135">AppDomainID</span></span>|<span data-ttu-id="ae0d9-136">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-136">win:UInt64</span></span>|<span data-ttu-id="ae0d9-137">Identifikátor domény aplikace, pro kterou je hlášena aktivita vlákna</span><span class="sxs-lookup"><span data-stu-id="ae0d9-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="ae0d9-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="ae0d9-138">Flags</span></span>|<span data-ttu-id="ae0d9-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ae0d9-139">win:UInt32</span></span>|<span data-ttu-id="ae0d9-140">Příznaky vytvoření vlákna.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="ae0d9-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="ae0d9-141">ManagedThreadIndex</span></span>|<span data-ttu-id="ae0d9-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ae0d9-142">win:UInt32</span></span>|<span data-ttu-id="ae0d9-143">Spravovaný index vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="ae0d9-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-144">OSThreadID</span></span>|<span data-ttu-id="ae0d9-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ae0d9-145">win:UInt32</span></span>|<span data-ttu-id="ae0d9-146">ID operačního systému vytvořeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="ae0d9-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-147">ClrInstanceID</span></span>|<span data-ttu-id="ae0d9-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ae0d9-148">win:UInt16</span></span>|<span data-ttu-id="ae0d9-149">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae0d9-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ae0d9-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="ae0d9-151">Událost AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="ae0d9-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="ae0d9-152">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae0d9-153">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-153">Keyword for raising the event</span></span>|<span data-ttu-id="ae0d9-154">Level</span><span class="sxs-lookup"><span data-stu-id="ae0d9-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae0d9-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ae0d9-156">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="ae0d9-157">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae0d9-158">Událost</span><span class="sxs-lookup"><span data-stu-id="ae0d9-158">Event</span></span>|<span data-ttu-id="ae0d9-159">ID události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-159">Event ID</span></span>|<span data-ttu-id="ae0d9-160">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ae0d9-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="ae0d9-161">83</span><span class="sxs-lookup"><span data-stu-id="ae0d9-161">83</span></span>|<span data-ttu-id="ae0d9-162">V aplikační doméně je přiděleno každé 4 MB paměti (přibližně).</span><span class="sxs-lookup"><span data-stu-id="ae0d9-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="ae0d9-163">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae0d9-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="ae0d9-164">Field name</span></span>|<span data-ttu-id="ae0d9-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ae0d9-165">Data type</span></span>|<span data-ttu-id="ae0d9-166">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0d9-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae0d9-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-167">AppDomainID</span></span>|<span data-ttu-id="ae0d9-168">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-168">win:UInt64</span></span>|<span data-ttu-id="ae0d9-169">Identifikátor domény aplikace, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="ae0d9-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="ae0d9-170">Přidělování</span><span class="sxs-lookup"><span data-stu-id="ae0d9-170">Allocated</span></span>|<span data-ttu-id="ae0d9-171">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-171">win:UInt64</span></span>|<span data-ttu-id="ae0d9-172">Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečteno).</span><span class="sxs-lookup"><span data-stu-id="ae0d9-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="ae0d9-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-173">ClrInstanceID</span></span>|<span data-ttu-id="ae0d9-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ae0d9-174">win:UInt16</span></span>|<span data-ttu-id="ae0d9-175">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae0d9-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ae0d9-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="ae0d9-177">Událost AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="ae0d9-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="ae0d9-178">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae0d9-179">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-179">Keyword for raising the event</span></span>|<span data-ttu-id="ae0d9-180">Level</span><span class="sxs-lookup"><span data-stu-id="ae0d9-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae0d9-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ae0d9-182">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="ae0d9-183">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae0d9-184">Událost</span><span class="sxs-lookup"><span data-stu-id="ae0d9-184">Event</span></span>|<span data-ttu-id="ae0d9-185">ID události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-185">Event ID</span></span>|<span data-ttu-id="ae0d9-186">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ae0d9-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="ae0d9-187">84</span><span class="sxs-lookup"><span data-stu-id="ae0d9-187">84</span></span>|<span data-ttu-id="ae0d9-188">Každé uvolnění paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="ae0d9-189">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae0d9-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="ae0d9-190">Field name</span></span>|<span data-ttu-id="ae0d9-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ae0d9-191">Data type</span></span>|<span data-ttu-id="ae0d9-192">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0d9-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae0d9-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-193">AppDomainID</span></span>|<span data-ttu-id="ae0d9-194">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-194">win:UInt64</span></span>|<span data-ttu-id="ae0d9-195">Identifikátor domény, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="ae0d9-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="ae0d9-196">Zachované</span><span class="sxs-lookup"><span data-stu-id="ae0d9-196">Survived</span></span>|<span data-ttu-id="ae0d9-197">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-197">win:UInt64</span></span>|<span data-ttu-id="ae0d9-198">Počet bajtů, které byly zachovány po poslední kolekci a které jsou známy pro tuto doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="ae0d9-199">Toto číslo je přesné a úplné po úplné kolekci, ale po dočasné kolekci může být neúplné.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="ae0d9-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="ae0d9-200">ProcessSurvived</span></span>|<span data-ttu-id="ae0d9-201">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-201">win:UInt64</span></span>|<span data-ttu-id="ae0d9-202">Celkový počet bajtů, které byly zachovány z poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="ae0d9-203">Po úplné kolekci představuje toto číslo počet bajtů, které se ve spravovaných haldách uchovávají živě.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="ae0d9-204">Po dočasné kolekci představuje toto číslo počet bajtů uchovávaných v dočasných generacích.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="ae0d9-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-205">ClrInstanceID</span></span>|<span data-ttu-id="ae0d9-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ae0d9-206">win:UInt16</span></span>|<span data-ttu-id="ae0d9-207">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae0d9-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ae0d9-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="ae0d9-209">Událost ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="ae0d9-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="ae0d9-210">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae0d9-211">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-211">Keyword for raising the event</span></span>|<span data-ttu-id="ae0d9-212">Level</span><span class="sxs-lookup"><span data-stu-id="ae0d9-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae0d9-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ae0d9-214">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-214">Informational(4)</span></span>|  
|<span data-ttu-id="ae0d9-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ae0d9-216">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="ae0d9-217">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae0d9-218">Událost</span><span class="sxs-lookup"><span data-stu-id="ae0d9-218">Event</span></span>|<span data-ttu-id="ae0d9-219">ID události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-219">Event ID</span></span>|<span data-ttu-id="ae0d9-220">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ae0d9-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="ae0d9-221">87</span><span class="sxs-lookup"><span data-stu-id="ae0d9-221">87</span></span>|<span data-ttu-id="ae0d9-222">Vlákno vstoupí do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="ae0d9-223">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae0d9-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="ae0d9-224">Field name</span></span>|<span data-ttu-id="ae0d9-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ae0d9-225">Data type</span></span>|<span data-ttu-id="ae0d9-226">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0d9-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae0d9-227">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="ae0d9-227">ThreadID</span></span>|<span data-ttu-id="ae0d9-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-228">win:UInt64</span></span>|<span data-ttu-id="ae0d9-229">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-229">The thread identifier.</span></span>|  
|<span data-ttu-id="ae0d9-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-230">AppDomainID</span></span>|<span data-ttu-id="ae0d9-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-231">win:UInt64</span></span>|<span data-ttu-id="ae0d9-232">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ae0d9-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="ae0d9-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-233">ClrInstanceID</span></span>|<span data-ttu-id="ae0d9-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ae0d9-234">win:UInt16</span></span>|<span data-ttu-id="ae0d9-235">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ae0d9-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ae0d9-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="ae0d9-237">Událost ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="ae0d9-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="ae0d9-238">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ae0d9-239">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-239">Keyword for raising the event</span></span>|<span data-ttu-id="ae0d9-240">Level</span><span class="sxs-lookup"><span data-stu-id="ae0d9-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae0d9-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="ae0d9-242">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-242">Informational(4)</span></span>|  
|<span data-ttu-id="ae0d9-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="ae0d9-244">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ae0d9-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="ae0d9-245">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae0d9-246">Událost</span><span class="sxs-lookup"><span data-stu-id="ae0d9-246">Event</span></span>|<span data-ttu-id="ae0d9-247">ID události</span><span class="sxs-lookup"><span data-stu-id="ae0d9-247">Event ID</span></span>|<span data-ttu-id="ae0d9-248">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ae0d9-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="ae0d9-249">86</span><span class="sxs-lookup"><span data-stu-id="ae0d9-249">86</span></span>|<span data-ttu-id="ae0d9-250">Vlákno se ukončí.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="ae0d9-251">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="ae0d9-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="ae0d9-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="ae0d9-252">Field name</span></span>|<span data-ttu-id="ae0d9-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ae0d9-253">Data type</span></span>|<span data-ttu-id="ae0d9-254">Popis</span><span class="sxs-lookup"><span data-stu-id="ae0d9-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae0d9-255">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="ae0d9-255">ThreadID</span></span>|<span data-ttu-id="ae0d9-256">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-256">win:UInt64</span></span>|<span data-ttu-id="ae0d9-257">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-257">The thread identifier.</span></span>|  
|<span data-ttu-id="ae0d9-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-258">AppDomainID</span></span>|<span data-ttu-id="ae0d9-259">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ae0d9-259">win:UInt64</span></span>|<span data-ttu-id="ae0d9-260">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ae0d9-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="ae0d9-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae0d9-261">ClrInstanceID</span></span>|<span data-ttu-id="ae0d9-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ae0d9-262">win:UInt16</span></span>|<span data-ttu-id="ae0d9-263">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ae0d9-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae0d9-264">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae0d9-264">See also</span></span>

- [<span data-ttu-id="ae0d9-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="ae0d9-265">CLR ETW Events</span></span>](clr-etw-events.md)
