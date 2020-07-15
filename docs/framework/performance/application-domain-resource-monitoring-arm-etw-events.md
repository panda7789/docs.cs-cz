---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
description: Přečtěte si o událostech trasování událostí pro Windows v doméně aplikace (ARM) v rozhraní .NET, například ThreadCreated –, AppDomainMemAllocated, AppDomainMemSurvived a další.
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: d118b3196b019a804df5399464cb86f7492c61b0
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309778"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="aba02-103">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="aba02-103">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="aba02-104">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aba02-104">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="aba02-105">Tyto události můžete použít, nebo můžete použít funkci monitorování prostředků domény aplikace (ARM) a získat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="aba02-105">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="aba02-106">Událost ThreadCreated –</span><span class="sxs-lookup"><span data-stu-id="aba02-106">ThreadCreated Event</span></span>

<span data-ttu-id="aba02-107">Tato událost se taky vyvolala pod poskytovatelem doběhu jako `ThreadDC` (pod `AppDomainResourceManagementRundownKeyword` klíčovým slovem).</span><span class="sxs-lookup"><span data-stu-id="aba02-107">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="aba02-108">Toto je jediná událost, která je vyvolána v rámci poskytovatele doběhu v této kategorii.</span><span class="sxs-lookup"><span data-stu-id="aba02-108">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="aba02-109">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="aba02-109">The following table shows the keyword and level.</span></span> <span data-ttu-id="aba02-110">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="aba02-110">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="aba02-111">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="aba02-111">Keyword for raising the event</span></span>|<span data-ttu-id="aba02-112">Level</span><span class="sxs-lookup"><span data-stu-id="aba02-112">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aba02-113">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aba02-113">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aba02-114">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-114">Informational(4)</span></span>|
|<span data-ttu-id="aba02-115">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="aba02-115">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aba02-116">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-116">Informational(4)</span></span>|

<span data-ttu-id="aba02-117">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="aba02-117">The following table shows the event information:</span></span>

|<span data-ttu-id="aba02-118">Událost</span><span class="sxs-lookup"><span data-stu-id="aba02-118">Event</span></span>|<span data-ttu-id="aba02-119">ID události</span><span class="sxs-lookup"><span data-stu-id="aba02-119">Event ID</span></span>|<span data-ttu-id="aba02-120">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="aba02-120">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="aba02-121">85</span><span class="sxs-lookup"><span data-stu-id="aba02-121">85</span></span>|<span data-ttu-id="aba02-122">Bylo vytvořeno vlákno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="aba02-122">A thread was created for the application domain.</span></span>|

<span data-ttu-id="aba02-123">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="aba02-123">The following table shows the event data:</span></span>

|<span data-ttu-id="aba02-124">Název pole</span><span class="sxs-lookup"><span data-stu-id="aba02-124">Field name</span></span>|<span data-ttu-id="aba02-125">Datový typ</span><span class="sxs-lookup"><span data-stu-id="aba02-125">Data type</span></span>|<span data-ttu-id="aba02-126">Popis</span><span class="sxs-lookup"><span data-stu-id="aba02-126">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="aba02-127">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="aba02-127">ThreadID</span></span>|<span data-ttu-id="aba02-128">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-128">win:UInt64</span></span>|<span data-ttu-id="aba02-129">ID vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="aba02-129">ID of the thread that was created.</span></span>|
|<span data-ttu-id="aba02-130">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aba02-130">AppDomainID</span></span>|<span data-ttu-id="aba02-131">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-131">win:UInt64</span></span>|<span data-ttu-id="aba02-132">Identifikátor domény aplikace, pro kterou je hlášena aktivita vlákna</span><span class="sxs-lookup"><span data-stu-id="aba02-132">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="aba02-133">Příznaky</span><span class="sxs-lookup"><span data-stu-id="aba02-133">Flags</span></span>|<span data-ttu-id="aba02-134">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aba02-134">win:UInt32</span></span>|<span data-ttu-id="aba02-135">Příznaky vytvoření vlákna.</span><span class="sxs-lookup"><span data-stu-id="aba02-135">Thread creation flags.</span></span>|
|<span data-ttu-id="aba02-136">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="aba02-136">ManagedThreadIndex</span></span>|<span data-ttu-id="aba02-137">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aba02-137">win:UInt32</span></span>|<span data-ttu-id="aba02-138">Spravovaný index vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="aba02-138">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="aba02-139">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="aba02-139">OSThreadID</span></span>|<span data-ttu-id="aba02-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="aba02-140">win:UInt32</span></span>|<span data-ttu-id="aba02-141">ID operačního systému vytvořeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="aba02-141">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="aba02-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aba02-142">ClrInstanceID</span></span>|<span data-ttu-id="aba02-143">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aba02-143">win:UInt16</span></span>|<span data-ttu-id="aba02-144">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aba02-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="aba02-145">Událost AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="aba02-145">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="aba02-146">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="aba02-146">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="aba02-147">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="aba02-147">Keyword for raising the event</span></span>|<span data-ttu-id="aba02-148">Level</span><span class="sxs-lookup"><span data-stu-id="aba02-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aba02-149">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aba02-149">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aba02-150">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-150">Informational(4)</span></span>|

<span data-ttu-id="aba02-151">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="aba02-151">The following table shows the event information:</span></span>

|<span data-ttu-id="aba02-152">Událost</span><span class="sxs-lookup"><span data-stu-id="aba02-152">Event</span></span>|<span data-ttu-id="aba02-153">ID události</span><span class="sxs-lookup"><span data-stu-id="aba02-153">Event ID</span></span>|<span data-ttu-id="aba02-154">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="aba02-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="aba02-155">83</span><span class="sxs-lookup"><span data-stu-id="aba02-155">83</span></span>|<span data-ttu-id="aba02-156">V aplikační doméně je přiděleno každé 4 MB paměti (přibližně).</span><span class="sxs-lookup"><span data-stu-id="aba02-156">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="aba02-157">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="aba02-157">The following table shows the event data:</span></span>

|<span data-ttu-id="aba02-158">Název pole</span><span class="sxs-lookup"><span data-stu-id="aba02-158">Field name</span></span>|<span data-ttu-id="aba02-159">Datový typ</span><span class="sxs-lookup"><span data-stu-id="aba02-159">Data type</span></span>|<span data-ttu-id="aba02-160">Popis</span><span class="sxs-lookup"><span data-stu-id="aba02-160">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="aba02-161">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aba02-161">AppDomainID</span></span>|<span data-ttu-id="aba02-162">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-162">win:UInt64</span></span>|<span data-ttu-id="aba02-163">Identifikátor domény aplikace, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="aba02-163">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="aba02-164">Přidělování</span><span class="sxs-lookup"><span data-stu-id="aba02-164">Allocated</span></span>|<span data-ttu-id="aba02-165">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-165">win:UInt64</span></span>|<span data-ttu-id="aba02-166">Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečteno).</span><span class="sxs-lookup"><span data-stu-id="aba02-166">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="aba02-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aba02-167">ClrInstanceID</span></span>|<span data-ttu-id="aba02-168">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aba02-168">win:UInt16</span></span>|<span data-ttu-id="aba02-169">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aba02-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="aba02-170">Událost AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="aba02-170">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="aba02-171">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="aba02-171">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="aba02-172">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="aba02-172">Keyword for raising the event</span></span>|<span data-ttu-id="aba02-173">Level</span><span class="sxs-lookup"><span data-stu-id="aba02-173">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aba02-174">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aba02-174">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aba02-175">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-175">Informational(4)</span></span>|

<span data-ttu-id="aba02-176">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="aba02-176">The following table shows the event information:</span></span>

|<span data-ttu-id="aba02-177">Událost</span><span class="sxs-lookup"><span data-stu-id="aba02-177">Event</span></span>|<span data-ttu-id="aba02-178">ID události</span><span class="sxs-lookup"><span data-stu-id="aba02-178">Event ID</span></span>|<span data-ttu-id="aba02-179">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="aba02-179">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="aba02-180">84</span><span class="sxs-lookup"><span data-stu-id="aba02-180">84</span></span>|<span data-ttu-id="aba02-181">Každé uvolnění paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="aba02-181">Each garbage collection has ended.</span></span>|

<span data-ttu-id="aba02-182">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="aba02-182">The following table shows the event data:</span></span>

|<span data-ttu-id="aba02-183">Název pole</span><span class="sxs-lookup"><span data-stu-id="aba02-183">Field name</span></span>|<span data-ttu-id="aba02-184">Datový typ</span><span class="sxs-lookup"><span data-stu-id="aba02-184">Data type</span></span>|<span data-ttu-id="aba02-185">Popis</span><span class="sxs-lookup"><span data-stu-id="aba02-185">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="aba02-186">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aba02-186">AppDomainID</span></span>|<span data-ttu-id="aba02-187">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-187">win:UInt64</span></span>|<span data-ttu-id="aba02-188">Identifikátor domény, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="aba02-188">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="aba02-189">Zachované</span><span class="sxs-lookup"><span data-stu-id="aba02-189">Survived</span></span>|<span data-ttu-id="aba02-190">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-190">win:UInt64</span></span>|<span data-ttu-id="aba02-191">Počet bajtů, které byly zachovány po poslední kolekci a které jsou známy pro tuto doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="aba02-191">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="aba02-192">Toto číslo je přesné a úplné po úplné kolekci, ale po dočasné kolekci může být neúplné.</span><span class="sxs-lookup"><span data-stu-id="aba02-192">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="aba02-193">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="aba02-193">ProcessSurvived</span></span>|<span data-ttu-id="aba02-194">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-194">win:UInt64</span></span>|<span data-ttu-id="aba02-195">Celkový počet bajtů, které byly zachovány z poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="aba02-195">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="aba02-196">Po úplné kolekci představuje toto číslo počet bajtů, které se ve spravovaných haldách uchovávají živě.</span><span class="sxs-lookup"><span data-stu-id="aba02-196">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="aba02-197">Po dočasné kolekci představuje toto číslo počet bajtů uchovávaných v dočasných generacích.</span><span class="sxs-lookup"><span data-stu-id="aba02-197">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="aba02-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aba02-198">ClrInstanceID</span></span>|<span data-ttu-id="aba02-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aba02-199">win:UInt16</span></span>|<span data-ttu-id="aba02-200">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aba02-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="aba02-201">Událost ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="aba02-201">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="aba02-202">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="aba02-202">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="aba02-203">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="aba02-203">Keyword for raising the event</span></span>|<span data-ttu-id="aba02-204">Level</span><span class="sxs-lookup"><span data-stu-id="aba02-204">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aba02-205">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aba02-205">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aba02-206">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-206">Informational(4)</span></span>|
|<span data-ttu-id="aba02-207">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="aba02-207">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aba02-208">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-208">Informational(4)</span></span>|

<span data-ttu-id="aba02-209">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="aba02-209">The following table shows the event information:</span></span>

|<span data-ttu-id="aba02-210">Událost</span><span class="sxs-lookup"><span data-stu-id="aba02-210">Event</span></span>|<span data-ttu-id="aba02-211">ID události</span><span class="sxs-lookup"><span data-stu-id="aba02-211">Event ID</span></span>|<span data-ttu-id="aba02-212">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="aba02-212">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="aba02-213">87</span><span class="sxs-lookup"><span data-stu-id="aba02-213">87</span></span>|<span data-ttu-id="aba02-214">Vlákno vstoupí do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="aba02-214">A thread enters an application domain.</span></span>|

<span data-ttu-id="aba02-215">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="aba02-215">The following table shows the event data:</span></span>

|<span data-ttu-id="aba02-216">Název pole</span><span class="sxs-lookup"><span data-stu-id="aba02-216">Field name</span></span>|<span data-ttu-id="aba02-217">Datový typ</span><span class="sxs-lookup"><span data-stu-id="aba02-217">Data type</span></span>|<span data-ttu-id="aba02-218">Popis</span><span class="sxs-lookup"><span data-stu-id="aba02-218">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="aba02-219">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="aba02-219">ThreadID</span></span>|<span data-ttu-id="aba02-220">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-220">win:UInt64</span></span>|<span data-ttu-id="aba02-221">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="aba02-221">The thread identifier.</span></span>|
|<span data-ttu-id="aba02-222">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aba02-222">AppDomainID</span></span>|<span data-ttu-id="aba02-223">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-223">win:UInt64</span></span>|<span data-ttu-id="aba02-224">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aba02-224">The application domain identifier.</span></span>|
|<span data-ttu-id="aba02-225">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aba02-225">ClrInstanceID</span></span>|<span data-ttu-id="aba02-226">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aba02-226">win:UInt16</span></span>|<span data-ttu-id="aba02-227">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aba02-227">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="aba02-228">Událost ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="aba02-228">ThreadTerminated Event</span></span>

<span data-ttu-id="aba02-229">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="aba02-229">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="aba02-230">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="aba02-230">Keyword for raising the event</span></span>|<span data-ttu-id="aba02-231">Level</span><span class="sxs-lookup"><span data-stu-id="aba02-231">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="aba02-232">`AppDomainResourceManagementKeyword`(0x800)</span><span class="sxs-lookup"><span data-stu-id="aba02-232">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="aba02-233">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-233">Informational(4)</span></span>|
|<span data-ttu-id="aba02-234">`ThreadingKeyword`(0x10000)</span><span class="sxs-lookup"><span data-stu-id="aba02-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="aba02-235">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="aba02-235">Informational(4)</span></span>|

<span data-ttu-id="aba02-236">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="aba02-236">The following table shows the event information:</span></span>

|<span data-ttu-id="aba02-237">Událost</span><span class="sxs-lookup"><span data-stu-id="aba02-237">Event</span></span>|<span data-ttu-id="aba02-238">ID události</span><span class="sxs-lookup"><span data-stu-id="aba02-238">Event ID</span></span>|<span data-ttu-id="aba02-239">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="aba02-239">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="aba02-240">86</span><span class="sxs-lookup"><span data-stu-id="aba02-240">86</span></span>|<span data-ttu-id="aba02-241">Vlákno se ukončí.</span><span class="sxs-lookup"><span data-stu-id="aba02-241">A thread terminates.</span></span>|

<span data-ttu-id="aba02-242">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="aba02-242">The following table shows the event data:</span></span>

|<span data-ttu-id="aba02-243">Název pole</span><span class="sxs-lookup"><span data-stu-id="aba02-243">Field name</span></span>|<span data-ttu-id="aba02-244">Datový typ</span><span class="sxs-lookup"><span data-stu-id="aba02-244">Data type</span></span>|<span data-ttu-id="aba02-245">Popis</span><span class="sxs-lookup"><span data-stu-id="aba02-245">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="aba02-246">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="aba02-246">ThreadID</span></span>|<span data-ttu-id="aba02-247">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-247">win:UInt64</span></span>|<span data-ttu-id="aba02-248">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="aba02-248">The thread identifier.</span></span>|
|<span data-ttu-id="aba02-249">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="aba02-249">AppDomainID</span></span>|<span data-ttu-id="aba02-250">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="aba02-250">win:UInt64</span></span>|<span data-ttu-id="aba02-251">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aba02-251">The application domain identifier.</span></span>|
|<span data-ttu-id="aba02-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aba02-252">ClrInstanceID</span></span>|<span data-ttu-id="aba02-253">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="aba02-253">win:UInt16</span></span>|<span data-ttu-id="aba02-254">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="aba02-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="aba02-255">Viz také</span><span class="sxs-lookup"><span data-stu-id="aba02-255">See also</span></span>

- [<span data-ttu-id="aba02-256">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="aba02-256">CLR ETW Events</span></span>](clr-etw-events.md)
