---
title: Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
ms.openlocfilehash: 0e453b2bafffd9e07a1bdddd97282c5b97f5483d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716219"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a><span data-ttu-id="c0b3d-102">Události Trasování událostí pro Windows sledování prostředků domény aplikace (ARM)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-102">Application Domain Resource Monitoring (ARM) ETW Events</span></span>

<span data-ttu-id="c0b3d-103">Tyto události poskytují podrobné diagnostické informace o stavu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-103">These events provide detailed diagnostic information about the state of an application domain.</span></span> <span data-ttu-id="c0b3d-104">Tyto události můžete použít, nebo můžete použít funkci monitorování prostředků domény aplikace (ARM) a získat stejné informace.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-104">You can use these events or use the application domain resource monitoring (ARM) feature to obtain the same information.</span></span>

## <a name="threadcreated-event"></a><span data-ttu-id="c0b3d-105">Událost ThreadCreated –</span><span class="sxs-lookup"><span data-stu-id="c0b3d-105">ThreadCreated Event</span></span>

<span data-ttu-id="c0b3d-106">Tato událost je vyvolána také v rámci poskytovatele doběhu jako `ThreadDC` (pod klíčovým slovem `AppDomainResourceManagementRundownKeyword`).</span><span class="sxs-lookup"><span data-stu-id="c0b3d-106">This event is also raised  under the rundown provider as `ThreadDC` (under the `AppDomainResourceManagementRundownKeyword` keyword).</span></span> <span data-ttu-id="c0b3d-107">Toto je jediná událost, která je vyvolána v rámci poskytovatele doběhu v této kategorii.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-107">This is the only event that is raised under the rundown provider in this category.</span></span>

<span data-ttu-id="c0b3d-108">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="c0b3d-109">Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c0b3d-109">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="c0b3d-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-110">Keyword for raising the event</span></span>|<span data-ttu-id="c0b3d-111">Úroveň</span><span class="sxs-lookup"><span data-stu-id="c0b3d-111">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c0b3d-112">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-112">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c0b3d-113">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-113">Informational(4)</span></span>|
|<span data-ttu-id="c0b3d-114">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-114">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c0b3d-115">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-115">Informational(4)</span></span>|

<span data-ttu-id="c0b3d-116">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-116">The following table shows the event information:</span></span>

|<span data-ttu-id="c0b3d-117">Událost</span><span class="sxs-lookup"><span data-stu-id="c0b3d-117">Event</span></span>|<span data-ttu-id="c0b3d-118">ID události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-118">Event ID</span></span>|<span data-ttu-id="c0b3d-119">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c0b3d-119">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadCreated`|<span data-ttu-id="c0b3d-120">85</span><span class="sxs-lookup"><span data-stu-id="c0b3d-120">85</span></span>|<span data-ttu-id="c0b3d-121">Bylo vytvořeno vlákno pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-121">A thread was created for the application domain.</span></span>|

<span data-ttu-id="c0b3d-122">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-122">The following table shows the event data:</span></span>

|<span data-ttu-id="c0b3d-123">Název pole</span><span class="sxs-lookup"><span data-stu-id="c0b3d-123">Field name</span></span>|<span data-ttu-id="c0b3d-124">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b3d-124">Data type</span></span>|<span data-ttu-id="c0b3d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b3d-125">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c0b3d-126">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="c0b3d-126">ThreadID</span></span>|<span data-ttu-id="c0b3d-127">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-127">win:UInt64</span></span>|<span data-ttu-id="c0b3d-128">ID vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-128">ID of the thread that was created.</span></span>|
|<span data-ttu-id="c0b3d-129">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-129">AppDomainID</span></span>|<span data-ttu-id="c0b3d-130">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-130">win:UInt64</span></span>|<span data-ttu-id="c0b3d-131">Identifikátor domény aplikace, pro kterou je hlášena aktivita vlákna</span><span class="sxs-lookup"><span data-stu-id="c0b3d-131">Identifier of the application domain for which thread activity is being reported.</span></span>|
|<span data-ttu-id="c0b3d-132">Příznaky</span><span class="sxs-lookup"><span data-stu-id="c0b3d-132">Flags</span></span>|<span data-ttu-id="c0b3d-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c0b3d-133">win:UInt32</span></span>|<span data-ttu-id="c0b3d-134">Příznaky vytvoření vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-134">Thread creation flags.</span></span>|
|<span data-ttu-id="c0b3d-135">ManagedThreadIndex</span><span class="sxs-lookup"><span data-stu-id="c0b3d-135">ManagedThreadIndex</span></span>|<span data-ttu-id="c0b3d-136">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c0b3d-136">win:UInt32</span></span>|<span data-ttu-id="c0b3d-137">Spravovaný index vlákna, které bylo vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-137">Managed index of the thread that was created.</span></span>|
|<span data-ttu-id="c0b3d-138">OSThreadID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-138">OSThreadID</span></span>|<span data-ttu-id="c0b3d-139">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="c0b3d-139">win:UInt32</span></span>|<span data-ttu-id="c0b3d-140">ID operačního systému vytvořeného vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-140">Operating system ID of the thread that was created.</span></span>|
|<span data-ttu-id="c0b3d-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-141">ClrInstanceID</span></span>|<span data-ttu-id="c0b3d-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b3d-142">win:UInt16</span></span>|<span data-ttu-id="c0b3d-143">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemallocated-event"></a><span data-ttu-id="c0b3d-144">Událost AppDomainMemAllocated</span><span class="sxs-lookup"><span data-stu-id="c0b3d-144">AppDomainMemAllocated Event</span></span>

<span data-ttu-id="c0b3d-145">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-145">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c0b3d-146">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-146">Keyword for raising the event</span></span>|<span data-ttu-id="c0b3d-147">Úroveň</span><span class="sxs-lookup"><span data-stu-id="c0b3d-147">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c0b3d-148">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-148">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c0b3d-149">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-149">Informational(4)</span></span>|

<span data-ttu-id="c0b3d-150">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-150">The following table shows the event information:</span></span>

|<span data-ttu-id="c0b3d-151">Událost</span><span class="sxs-lookup"><span data-stu-id="c0b3d-151">Event</span></span>|<span data-ttu-id="c0b3d-152">ID události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-152">Event ID</span></span>|<span data-ttu-id="c0b3d-153">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c0b3d-153">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|<span data-ttu-id="c0b3d-154">83</span><span class="sxs-lookup"><span data-stu-id="c0b3d-154">83</span></span>|<span data-ttu-id="c0b3d-155">V aplikační doméně je přiděleno každé 4 MB paměti (přibližně).</span><span class="sxs-lookup"><span data-stu-id="c0b3d-155">Every 4 MB of memory (approximately) is allocated in the application domain.</span></span>|

<span data-ttu-id="c0b3d-156">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-156">The following table shows the event data:</span></span>

|<span data-ttu-id="c0b3d-157">Název pole</span><span class="sxs-lookup"><span data-stu-id="c0b3d-157">Field name</span></span>|<span data-ttu-id="c0b3d-158">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b3d-158">Data type</span></span>|<span data-ttu-id="c0b3d-159">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b3d-159">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c0b3d-160">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-160">AppDomainID</span></span>|<span data-ttu-id="c0b3d-161">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-161">win:UInt64</span></span>|<span data-ttu-id="c0b3d-162">Identifikátor domény aplikace, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="c0b3d-162">Identifier of the application domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="c0b3d-163">Přidělování</span><span class="sxs-lookup"><span data-stu-id="c0b3d-163">Allocated</span></span>|<span data-ttu-id="c0b3d-164">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-164">win:UInt64</span></span>|<span data-ttu-id="c0b3d-165">Celkový počet bajtů přidělených v této doméně aplikace od vytvoření domény aplikace (množství uvolněné paměti není odečteno).</span><span class="sxs-lookup"><span data-stu-id="c0b3d-165">The total number of bytes allocated in this application domain since the application domain was created (the amount of freed memory is not subtracted).</span></span>|
|<span data-ttu-id="c0b3d-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-166">ClrInstanceID</span></span>|<span data-ttu-id="c0b3d-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b3d-167">win:UInt16</span></span>|<span data-ttu-id="c0b3d-168">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="appdomainmemsurvived-event"></a><span data-ttu-id="c0b3d-169">Událost AppDomainMemSurvived</span><span class="sxs-lookup"><span data-stu-id="c0b3d-169">AppDomainMemSurvived Event</span></span>

<span data-ttu-id="c0b3d-170">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-170">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c0b3d-171">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-171">Keyword for raising the event</span></span>|<span data-ttu-id="c0b3d-172">Úroveň</span><span class="sxs-lookup"><span data-stu-id="c0b3d-172">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c0b3d-173">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-173">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c0b3d-174">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-174">Informational(4)</span></span>|

<span data-ttu-id="c0b3d-175">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-175">The following table shows the event information:</span></span>

|<span data-ttu-id="c0b3d-176">Událost</span><span class="sxs-lookup"><span data-stu-id="c0b3d-176">Event</span></span>|<span data-ttu-id="c0b3d-177">ID události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-177">Event ID</span></span>|<span data-ttu-id="c0b3d-178">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c0b3d-178">Raised when</span></span>|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|<span data-ttu-id="c0b3d-179">84</span><span class="sxs-lookup"><span data-stu-id="c0b3d-179">84</span></span>|<span data-ttu-id="c0b3d-180">Každé uvolnění paměti bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-180">Each garbage collection has ended.</span></span>|

<span data-ttu-id="c0b3d-181">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-181">The following table shows the event data:</span></span>

|<span data-ttu-id="c0b3d-182">Název pole</span><span class="sxs-lookup"><span data-stu-id="c0b3d-182">Field name</span></span>|<span data-ttu-id="c0b3d-183">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b3d-183">Data type</span></span>|<span data-ttu-id="c0b3d-184">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b3d-184">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c0b3d-185">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-185">AppDomainID</span></span>|<span data-ttu-id="c0b3d-186">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-186">win:UInt64</span></span>|<span data-ttu-id="c0b3d-187">Identifikátor domény, pro kterou se vykazuje využití prostředků</span><span class="sxs-lookup"><span data-stu-id="c0b3d-187">Identifier of the domain for which resource usage is being reported.</span></span>|
|<span data-ttu-id="c0b3d-188">Zachované</span><span class="sxs-lookup"><span data-stu-id="c0b3d-188">Survived</span></span>|<span data-ttu-id="c0b3d-189">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-189">win:UInt64</span></span>|<span data-ttu-id="c0b3d-190">Počet bajtů, které byly zachovány po poslední kolekci a které jsou známy pro tuto doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-190">The number of bytes that survived after the last collection and that are known to be held by this application domain.</span></span> <span data-ttu-id="c0b3d-191">Toto číslo je přesné a úplné po úplné kolekci, ale po dočasné kolekci může být neúplné.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-191">This number is accurate and complete after a full collection, but may be incomplete after an ephemeral collection.</span></span>|
|<span data-ttu-id="c0b3d-192">ProcessSurvived</span><span class="sxs-lookup"><span data-stu-id="c0b3d-192">ProcessSurvived</span></span>|<span data-ttu-id="c0b3d-193">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-193">win:UInt64</span></span>|<span data-ttu-id="c0b3d-194">Celkový počet bajtů, které byly zachovány z poslední kolekce.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-194">The total bytes that survived from the last collection.</span></span> <span data-ttu-id="c0b3d-195">Po úplné kolekci představuje toto číslo počet bajtů, které se ve spravovaných haldách uchovávají živě.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-195">After a full collection, this number represents the number of bytes being held live in managed heaps.</span></span> <span data-ttu-id="c0b3d-196">Po dočasné kolekci představuje toto číslo počet bajtů uchovávaných v dočasných generacích.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-196">After an ephemeral collection, this number represents the number of bytes held live in ephemeral generations.</span></span>|
|<span data-ttu-id="c0b3d-197">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-197">ClrInstanceID</span></span>|<span data-ttu-id="c0b3d-198">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b3d-198">win:UInt16</span></span>|<span data-ttu-id="c0b3d-199">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-199">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadappdomainenter-event"></a><span data-ttu-id="c0b3d-200">Událost ThreadAppDomainEnter</span><span class="sxs-lookup"><span data-stu-id="c0b3d-200">ThreadAppDomainEnter Event</span></span>

<span data-ttu-id="c0b3d-201">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-201">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c0b3d-202">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-202">Keyword for raising the event</span></span>|<span data-ttu-id="c0b3d-203">Úroveň</span><span class="sxs-lookup"><span data-stu-id="c0b3d-203">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c0b3d-204">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-204">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c0b3d-205">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-205">Informational(4)</span></span>|
|<span data-ttu-id="c0b3d-206">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-206">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c0b3d-207">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-207">Informational(4)</span></span>|

<span data-ttu-id="c0b3d-208">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-208">The following table shows the event information:</span></span>

|<span data-ttu-id="c0b3d-209">Událost</span><span class="sxs-lookup"><span data-stu-id="c0b3d-209">Event</span></span>|<span data-ttu-id="c0b3d-210">ID události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-210">Event ID</span></span>|<span data-ttu-id="c0b3d-211">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c0b3d-211">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|<span data-ttu-id="c0b3d-212">87</span><span class="sxs-lookup"><span data-stu-id="c0b3d-212">87</span></span>|<span data-ttu-id="c0b3d-213">Vlákno vstoupí do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-213">A thread enters an application domain.</span></span>|

<span data-ttu-id="c0b3d-214">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-214">The following table shows the event data:</span></span>

|<span data-ttu-id="c0b3d-215">Název pole</span><span class="sxs-lookup"><span data-stu-id="c0b3d-215">Field name</span></span>|<span data-ttu-id="c0b3d-216">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b3d-216">Data type</span></span>|<span data-ttu-id="c0b3d-217">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b3d-217">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c0b3d-218">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="c0b3d-218">ThreadID</span></span>|<span data-ttu-id="c0b3d-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-219">win:UInt64</span></span>|<span data-ttu-id="c0b3d-220">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-220">The thread identifier.</span></span>|
|<span data-ttu-id="c0b3d-221">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-221">AppDomainID</span></span>|<span data-ttu-id="c0b3d-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-222">win:UInt64</span></span>|<span data-ttu-id="c0b3d-223">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c0b3d-223">The application domain identifier.</span></span>|
|<span data-ttu-id="c0b3d-224">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-224">ClrInstanceID</span></span>|<span data-ttu-id="c0b3d-225">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b3d-225">win:UInt16</span></span>|<span data-ttu-id="c0b3d-226">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-226">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadterminated-event"></a><span data-ttu-id="c0b3d-227">Událost ThreadTerminated</span><span class="sxs-lookup"><span data-stu-id="c0b3d-227">ThreadTerminated Event</span></span>

<span data-ttu-id="c0b3d-228">Klíčové slovo a úroveň jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-228">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="c0b3d-229">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-229">Keyword for raising the event</span></span>|<span data-ttu-id="c0b3d-230">Úroveň</span><span class="sxs-lookup"><span data-stu-id="c0b3d-230">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="c0b3d-231">`AppDomainResourceManagementKeyword` (0x800)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-231">`AppDomainResourceManagementKeyword` (0x800)</span></span>|<span data-ttu-id="c0b3d-232">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-232">Informational(4)</span></span>|
|<span data-ttu-id="c0b3d-233">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-233">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="c0b3d-234">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="c0b3d-234">Informational(4)</span></span>|

<span data-ttu-id="c0b3d-235">Následující tabulka uvádí informace o událostech:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-235">The following table shows the event information:</span></span>

|<span data-ttu-id="c0b3d-236">Událost</span><span class="sxs-lookup"><span data-stu-id="c0b3d-236">Event</span></span>|<span data-ttu-id="c0b3d-237">ID události</span><span class="sxs-lookup"><span data-stu-id="c0b3d-237">Event ID</span></span>|<span data-ttu-id="c0b3d-238">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="c0b3d-238">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ThreadTerminated`|<span data-ttu-id="c0b3d-239">86</span><span class="sxs-lookup"><span data-stu-id="c0b3d-239">86</span></span>|<span data-ttu-id="c0b3d-240">Vlákno se ukončí.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-240">A thread terminates.</span></span>|

<span data-ttu-id="c0b3d-241">Následující tabulka ukazuje data události:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-241">The following table shows the event data:</span></span>

|<span data-ttu-id="c0b3d-242">Název pole</span><span class="sxs-lookup"><span data-stu-id="c0b3d-242">Field name</span></span>|<span data-ttu-id="c0b3d-243">Datový typ</span><span class="sxs-lookup"><span data-stu-id="c0b3d-243">Data type</span></span>|<span data-ttu-id="c0b3d-244">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b3d-244">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="c0b3d-245">IDvlákna</span><span class="sxs-lookup"><span data-stu-id="c0b3d-245">ThreadID</span></span>|<span data-ttu-id="c0b3d-246">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-246">win:UInt64</span></span>|<span data-ttu-id="c0b3d-247">Identifikátor vlákna.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-247">The thread identifier.</span></span>|
|<span data-ttu-id="c0b3d-248">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-248">AppDomainID</span></span>|<span data-ttu-id="c0b3d-249">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="c0b3d-249">win:UInt64</span></span>|<span data-ttu-id="c0b3d-250">Identifikátor domény aplikace</span><span class="sxs-lookup"><span data-stu-id="c0b3d-250">The application domain identifier.</span></span>|
|<span data-ttu-id="c0b3d-251">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b3d-251">ClrInstanceID</span></span>|<span data-ttu-id="c0b3d-252">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b3d-252">win:UInt16</span></span>|<span data-ttu-id="c0b3d-253">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c0b3d-253">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c0b3d-254">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0b3d-254">See also</span></span>

- [<span data-ttu-id="c0b3d-255">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="c0b3d-255">CLR ETW Events</span></span>](clr-etw-events.md)
