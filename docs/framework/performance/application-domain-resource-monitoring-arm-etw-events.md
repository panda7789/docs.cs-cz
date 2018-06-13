---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47ab6e52278c77156e828869dd23575561879bff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398180"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="dcd07-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="dcd07-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="dcd07-103">Tyto události poskytují podrobné diagnostické informace týkající se stavu služby domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="dcd07-104">Můžete použít tyto události nebo pomocí prostředků domény aplikace (ARM) funkci monitorování získat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>  
  
 <span data-ttu-id="dcd07-105">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="dcd07-105">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="dcd07-106">Threadcreated – událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-106">ThreadCreated Event</span></span>](#threadcreated_event)  
  
-   [<span data-ttu-id="dcd07-107">AppDomainMemAllocated událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-107">AppDomainMemAllocated Event</span></span>](#appdomainmemallocated_event)  
  
-   [<span data-ttu-id="dcd07-108">AppDomainMemSurvived událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-108">AppDomainMemSurvived Event</span></span>](#appdomainmemsurvived_event)  
  
-   [<span data-ttu-id="dcd07-109">ThreadAppDomainEnter událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-109">ThreadAppDomainEnter Event</span></span>](#threadappdomainenter_event)  
  
-   [<span data-ttu-id="dcd07-110">ThreadTerminated událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-110">ThreadTerminated Event</span></span>](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a><span data-ttu-id="dcd07-111">Threadcreated – událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-111">ThreadCreated Event</span></span>  
 <span data-ttu-id="dcd07-112">Tato událost je aktivována také v rámci sekvence daneho zprostředkovatele jako `ThreadDC` (v části `AppDomainResourceManagementRundownKeyword` – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="dcd07-112">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="dcd07-113">Toto je pouze událost, která se vyvolá v rámci sekvence daneho zprostředkovatele v této kategorii.</span><span class="sxs-lookup"><span data-stu-id="dcd07-113">This is the only event that is raised under the rundown provider in this category.</span></span>  
  
 <span data-ttu-id="dcd07-114">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="dcd07-114">The following table shows the keyword and level.</span></span> <span data-ttu-id="dcd07-115">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="dcd07-115">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="dcd07-116">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="dcd07-116">Keyword for raising the event</span></span>|<span data-ttu-id="dcd07-117">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd07-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dcd07-118">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dcd07-118">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dcd07-119">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-119">Informational(4)</span></span>|  
|<span data-ttu-id="dcd07-120">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dcd07-120">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dcd07-121">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-121">Informational(4)</span></span>|  
  
 <span data-ttu-id="dcd07-122">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="dcd07-122">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dcd07-123">Událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-123">Event</span></span>|<span data-ttu-id="dcd07-124">ID události</span><span class="sxs-lookup"><span data-stu-id="dcd07-124">Event ID</span></span>|<span data-ttu-id="dcd07-125">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="dcd07-125">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|<span data-ttu-id="dcd07-126">85</span><span class="sxs-lookup"><span data-stu-id="dcd07-126">85</span></span>|<span data-ttu-id="dcd07-127">Vlákno byl vytvořen pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-127">A thread was created for the application domain.</span></span>|  
  
 <span data-ttu-id="dcd07-128">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="dcd07-128">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dcd07-129">Název pole</span><span class="sxs-lookup"><span data-stu-id="dcd07-129">Field name</span></span>|<span data-ttu-id="dcd07-130">Datový typ</span><span class="sxs-lookup"><span data-stu-id="dcd07-130">Data type</span></span>|<span data-ttu-id="dcd07-131">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd07-131">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dcd07-132">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="dcd07-132">ThreadID</span></span>|<span data-ttu-id="dcd07-133">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-133">win:UInt64</span></span>|<span data-ttu-id="dcd07-134">ID vlákna, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="dcd07-134">ID of the thread that was created.</span></span>|  
|<span data-ttu-id="dcd07-135">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dcd07-135">AppDomainID</span></span>|<span data-ttu-id="dcd07-136">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-136">win:UInt64</span></span>|<span data-ttu-id="dcd07-137">Identifikátor doménu aplikace, pro které vlákno je hlášena aktivity.</span><span class="sxs-lookup"><span data-stu-id="dcd07-137">Identifier of the application domain for which thread activity is being reported.</span></span>|  
|<span data-ttu-id="dcd07-138">Příznaky</span><span class="sxs-lookup"><span data-stu-id="dcd07-138">Flags</span></span>|<span data-ttu-id="dcd07-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dcd07-139">win:UInt32</span></span>|<span data-ttu-id="dcd07-140">Vytvoření příznaky přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="dcd07-140">Thread creation flags.</span></span>|  
|<span data-ttu-id="dcd07-141">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="dcd07-141">ManagedThreadIndex</span></span>|<span data-ttu-id="dcd07-142">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dcd07-142">win:UInt32</span></span>|<span data-ttu-id="dcd07-143">Spravované index vláken, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="dcd07-143">Managed index of the thread that was created.</span></span>|  
|<span data-ttu-id="dcd07-144">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="dcd07-144">OSThreadID</span></span>|<span data-ttu-id="dcd07-145">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="dcd07-145">win:UInt32</span></span>|<span data-ttu-id="dcd07-146">Operační systém ID vlákna, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="dcd07-146">Operating system ID of the thread that was created.</span></span>|  
|<span data-ttu-id="dcd07-147">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dcd07-147">ClrInstanceID</span></span>|<span data-ttu-id="dcd07-148">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dcd07-148">win:UInt16</span></span>|<span data-ttu-id="dcd07-149">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dcd07-149">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="dcd07-150">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="dcd07-150">Back to top</span></span>](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a><span data-ttu-id="dcd07-151">AppDomainMemAllocated událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-151">AppDomainMemAllocated Event</span></span>  
 <span data-ttu-id="dcd07-152">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="dcd07-152">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dcd07-153">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="dcd07-153">Keyword for raising the event</span></span>|<span data-ttu-id="dcd07-154">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd07-154">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dcd07-155">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dcd07-155">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dcd07-156">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-156">Informational(4)</span></span>|  
  
 <span data-ttu-id="dcd07-157">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="dcd07-157">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dcd07-158">Událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-158">Event</span></span>|<span data-ttu-id="dcd07-159">ID události</span><span class="sxs-lookup"><span data-stu-id="dcd07-159">Event ID</span></span>|<span data-ttu-id="dcd07-160">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="dcd07-160">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|<span data-ttu-id="dcd07-161">83</span><span class="sxs-lookup"><span data-stu-id="dcd07-161">83</span></span>|<span data-ttu-id="dcd07-162">Každý 4 MB paměti (přibližně) je přidělen v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-162">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|  
  
 <span data-ttu-id="dcd07-163">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="dcd07-163">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dcd07-164">Název pole</span><span class="sxs-lookup"><span data-stu-id="dcd07-164">Field name</span></span>|<span data-ttu-id="dcd07-165">Datový typ</span><span class="sxs-lookup"><span data-stu-id="dcd07-165">Data type</span></span>|<span data-ttu-id="dcd07-166">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd07-166">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dcd07-167">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dcd07-167">AppDomainID</span></span>|<span data-ttu-id="dcd07-168">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-168">win:UInt64</span></span>|<span data-ttu-id="dcd07-169">Identifikátor doménu aplikace, pro který prostředek je hlášena využití.</span><span class="sxs-lookup"><span data-stu-id="dcd07-169">Identifier of the application domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="dcd07-170">Přidělené</span><span class="sxs-lookup"><span data-stu-id="dcd07-170">Allocated</span></span>|<span data-ttu-id="dcd07-171">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-171">win:UInt64</span></span>|<span data-ttu-id="dcd07-172">Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečítat).</span><span class="sxs-lookup"><span data-stu-id="dcd07-172">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|  
|<span data-ttu-id="dcd07-173">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dcd07-173">ClrInstanceID</span></span>|<span data-ttu-id="dcd07-174">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dcd07-174">win:UInt16</span></span>|<span data-ttu-id="dcd07-175">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dcd07-175">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="dcd07-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="dcd07-176">Back to top</span></span>](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="dcd07-177">AppDomainMemSurvived událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-177">AppDomainMemSurvived Event</span></span>  
 <span data-ttu-id="dcd07-178">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="dcd07-178">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dcd07-179">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="dcd07-179">Keyword for raising the event</span></span>|<span data-ttu-id="dcd07-180">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd07-180">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dcd07-181">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dcd07-181">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dcd07-182">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-182">Informational(4)</span></span>|  
  
 <span data-ttu-id="dcd07-183">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="dcd07-183">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dcd07-184">Událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-184">Event</span></span>|<span data-ttu-id="dcd07-185">ID události</span><span class="sxs-lookup"><span data-stu-id="dcd07-185">Event ID</span></span>|<span data-ttu-id="dcd07-186">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="dcd07-186">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|<span data-ttu-id="dcd07-187">84</span><span class="sxs-lookup"><span data-stu-id="dcd07-187">84</span></span>|<span data-ttu-id="dcd07-188">Uvolňování paměti jednotlivých byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="dcd07-188">Each garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="dcd07-189">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="dcd07-189">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dcd07-190">Název pole</span><span class="sxs-lookup"><span data-stu-id="dcd07-190">Field name</span></span>|<span data-ttu-id="dcd07-191">Datový typ</span><span class="sxs-lookup"><span data-stu-id="dcd07-191">Data type</span></span>|<span data-ttu-id="dcd07-192">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd07-192">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dcd07-193">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dcd07-193">AppDomainID</span></span>|<span data-ttu-id="dcd07-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-194">win:UInt64</span></span>|<span data-ttu-id="dcd07-195">Identifikátor domény, pro který prostředek je hlášena využití.</span><span class="sxs-lookup"><span data-stu-id="dcd07-195">Identifier of the domain for which resource usage is being reported.</span></span>|  
|<span data-ttu-id="dcd07-196">Zůstal naživu</span><span class="sxs-lookup"><span data-stu-id="dcd07-196">Survived</span></span>|<span data-ttu-id="dcd07-197">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-197">win:UInt64</span></span>|<span data-ttu-id="dcd07-198">Počet bajtů, který zůstal naživu po poslední kolekce a které jsou známé uchovávat tato doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-198">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="dcd07-199">Toto číslo je přesné a úplné po úplné kolekce, ale mohou být neúplné po dočasné kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcd07-199">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|  
|<span data-ttu-id="dcd07-200">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="dcd07-200">ProcessSurvived</span></span>|<span data-ttu-id="dcd07-201">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-201">win:UInt64</span></span>|<span data-ttu-id="dcd07-202">Celkový počet bajtů, které zůstal naživu z poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcd07-202">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="dcd07-203">Po kompletní sadu toto číslo představuje počet bajtů, se uchovávat za provozu ve spravovaných haldách.</span><span class="sxs-lookup"><span data-stu-id="dcd07-203">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="dcd07-204">Po dočasné kolekce toto číslo představuje počet bajtů uchovávat v dočasných generace za provozu.</span><span class="sxs-lookup"><span data-stu-id="dcd07-204">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|  
|<span data-ttu-id="dcd07-205">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dcd07-205">ClrInstanceID</span></span>|<span data-ttu-id="dcd07-206">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dcd07-206">win:UInt16</span></span>|<span data-ttu-id="dcd07-207">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dcd07-207">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="dcd07-208">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="dcd07-208">Back to top</span></span>](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a><span data-ttu-id="dcd07-209">ThreadAppDomainEnter událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-209">ThreadAppDomainEnter Event</span></span>  
 <span data-ttu-id="dcd07-210">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="dcd07-210">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dcd07-211">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="dcd07-211">Keyword for raising the event</span></span>|<span data-ttu-id="dcd07-212">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd07-212">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dcd07-213">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dcd07-213">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dcd07-214">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-214">Informational(4)</span></span>|  
|<span data-ttu-id="dcd07-215">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dcd07-215">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dcd07-216">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-216">Informational(4)</span></span>|  
  
 <span data-ttu-id="dcd07-217">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="dcd07-217">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dcd07-218">Událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-218">Event</span></span>|<span data-ttu-id="dcd07-219">ID události</span><span class="sxs-lookup"><span data-stu-id="dcd07-219">Event ID</span></span>|<span data-ttu-id="dcd07-220">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="dcd07-220">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|<span data-ttu-id="dcd07-221">87</span><span class="sxs-lookup"><span data-stu-id="dcd07-221">87</span></span>|<span data-ttu-id="dcd07-222">Vlákno vstupuje do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-222">A thread enters an application domain.</span></span>|  
  
 <span data-ttu-id="dcd07-223">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="dcd07-223">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="dcd07-224">Název pole</span><span class="sxs-lookup"><span data-stu-id="dcd07-224">Field name</span></span>|<span data-ttu-id="dcd07-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="dcd07-225">Data type</span></span>|<span data-ttu-id="dcd07-226">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd07-226">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dcd07-227">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="dcd07-227">ThreadID</span></span>|<span data-ttu-id="dcd07-228">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-228">win:UInt64</span></span>|<span data-ttu-id="dcd07-229">Identifikátor přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="dcd07-229">The thread identifier.</span></span>|  
|<span data-ttu-id="dcd07-230">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dcd07-230">AppDomainID</span></span>|<span data-ttu-id="dcd07-231">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-231">win:UInt64</span></span>|<span data-ttu-id="dcd07-232">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-232">The application domain identifier.</span></span>|  
|<span data-ttu-id="dcd07-233">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dcd07-233">ClrInstanceID</span></span>|<span data-ttu-id="dcd07-234">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dcd07-234">win:UInt16</span></span>|<span data-ttu-id="dcd07-235">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dcd07-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="dcd07-236">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="dcd07-236">Back to top</span></span>](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a><span data-ttu-id="dcd07-237">ThreadTerminated událostí</span><span class="sxs-lookup"><span data-stu-id="dcd07-237">ThreadTerminated Event</span></span>  
 <span data-ttu-id="dcd07-238">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="dcd07-238">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="dcd07-239">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="dcd07-239">Keyword for raising the event</span></span>|<span data-ttu-id="dcd07-240">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd07-240">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="dcd07-241">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="dcd07-241">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="dcd07-242">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-242">Informational(4)</span></span>|  
|<span data-ttu-id="dcd07-243">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="dcd07-243">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="dcd07-244">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="dcd07-244">Informational(4)</span></span>|  
  
 <span data-ttu-id="dcd07-245">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="dcd07-245">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="dcd07-246">Událost</span><span class="sxs-lookup"><span data-stu-id="dcd07-246">Event</span></span>|<span data-ttu-id="dcd07-247">ID události</span><span class="sxs-lookup"><span data-stu-id="dcd07-247">Event ID</span></span>|<span data-ttu-id="dcd07-248">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="dcd07-248">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|<span data-ttu-id="dcd07-249">86</span><span class="sxs-lookup"><span data-stu-id="dcd07-249">86</span></span>|<span data-ttu-id="dcd07-250">Vlákno ukončí.</span><span class="sxs-lookup"><span data-stu-id="dcd07-250">A thread terminates.</span></span>|  
  
 <span data-ttu-id="dcd07-251">Následující tabulka zobrazuje data událostí:</span><span class="sxs-lookup"><span data-stu-id="dcd07-251">The following table shows the event data:</span></span>  
  
|<span data-ttu-id="dcd07-252">Název pole</span><span class="sxs-lookup"><span data-stu-id="dcd07-252">Field name</span></span>|<span data-ttu-id="dcd07-253">Datový typ</span><span class="sxs-lookup"><span data-stu-id="dcd07-253">Data type</span></span>|<span data-ttu-id="dcd07-254">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd07-254">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="dcd07-255">ID podprocesu</span><span class="sxs-lookup"><span data-stu-id="dcd07-255">ThreadID</span></span>|<span data-ttu-id="dcd07-256">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-256">win:UInt64</span></span>|<span data-ttu-id="dcd07-257">Identifikátor přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="dcd07-257">The thread identifier.</span></span>|  
|<span data-ttu-id="dcd07-258">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="dcd07-258">AppDomainID</span></span>|<span data-ttu-id="dcd07-259">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="dcd07-259">win:UInt64</span></span>|<span data-ttu-id="dcd07-260">Identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="dcd07-260">The application domain identifier.</span></span>|  
|<span data-ttu-id="dcd07-261">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="dcd07-261">ClrInstanceID</span></span>|<span data-ttu-id="dcd07-262">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="dcd07-262">win:UInt16</span></span>|<span data-ttu-id="dcd07-263">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="dcd07-263">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcd07-264">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcd07-264">See Also</span></span>  
 [<span data-ttu-id="dcd07-265">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="dcd07-265">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
