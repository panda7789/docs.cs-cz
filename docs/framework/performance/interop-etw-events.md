---
title: "Události Trasování událostí pro Windows interoperability"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5670eb910406626096f776d3b4192e2d58d7ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="1f399-102">Události Trasování událostí pro Windows interoperability</span><span class="sxs-lookup"><span data-stu-id="1f399-102">Interop ETW Events</span></span>
<a name="top"></a><span data-ttu-id="1f399-103">Události interoperability zaznamenat informace o Microsoft (MSIL intermediate language) se zakázaným inzerováním generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1f399-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="1f399-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="1f399-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="1f399-105">ILStubGenerated událostí</span><span class="sxs-lookup"><span data-stu-id="1f399-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="1f399-106">ILStubCacheHit událostí</span><span class="sxs-lookup"><span data-stu-id="1f399-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="1f399-107">ILStubGenerated událostí</span><span class="sxs-lookup"><span data-stu-id="1f399-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="1f399-108">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="1f399-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="1f399-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="1f399-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1f399-110">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="1f399-110">Keyword for raising the event</span></span>|<span data-ttu-id="1f399-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="1f399-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1f399-112">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="1f399-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="1f399-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="1f399-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="1f399-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="1f399-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1f399-115">Událost</span><span class="sxs-lookup"><span data-stu-id="1f399-115">Event</span></span>|<span data-ttu-id="1f399-116">ID události</span><span class="sxs-lookup"><span data-stu-id="1f399-116">Event ID</span></span>|<span data-ttu-id="1f399-117">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="1f399-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="1f399-118">88</span><span class="sxs-lookup"><span data-stu-id="1f399-118">88</span></span>|<span data-ttu-id="1f399-119">MSIL stub byla vygenerována.</span><span class="sxs-lookup"><span data-stu-id="1f399-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="1f399-120">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="1f399-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1f399-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="1f399-121">Field name</span></span>|<span data-ttu-id="1f399-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1f399-122">Data type</span></span>|<span data-ttu-id="1f399-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1f399-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1f399-124">ID modulu</span><span class="sxs-lookup"><span data-stu-id="1f399-124">ModuleID</span></span>|<span data-ttu-id="1f399-125">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1f399-125">win:UInt16</span></span>|<span data-ttu-id="1f399-126">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="1f399-126">The module identifier.</span></span>|  
|<span data-ttu-id="1f399-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="1f399-127">StubMethodID</span></span>|<span data-ttu-id="1f399-128">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1f399-128">win:UInt64</span></span>|<span data-ttu-id="1f399-129">Identifikátor se zakázaným inzerováním metoda.</span><span class="sxs-lookup"><span data-stu-id="1f399-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="1f399-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="1f399-130">StubFlags</span></span>|<span data-ttu-id="1f399-131">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1f399-131">win:UInt64</span></span>|<span data-ttu-id="1f399-132">Příznaky pro testovací kód:</span><span class="sxs-lookup"><span data-stu-id="1f399-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="1f399-133">0x1 - zpětné zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1f399-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="1f399-134">0x2 - zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="1f399-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="1f399-135">0x4 - stub generované NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="1f399-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="1f399-136">0x8 - delegáta.</span><span class="sxs-lookup"><span data-stu-id="1f399-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="1f399-137">0x10 - proměnné arrgument.</span><span class="sxs-lookup"><span data-stu-id="1f399-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="1f399-138">0x20 – nespravované volaný.</span><span class="sxs-lookup"><span data-stu-id="1f399-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="1f399-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="1f399-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="1f399-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1f399-140">win:UInt32</span></span>|<span data-ttu-id="1f399-141">Token pro metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1f399-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="1f399-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="1f399-143">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-143">win:UnicodeString</span></span>|<span data-ttu-id="1f399-144">Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1f399-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="1f399-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="1f399-146">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-146">win:UnicodeString</span></span>|<span data-ttu-id="1f399-147">Název spravovaného zprostředkovatele komunikace s objekty metody.</span><span class="sxs-lookup"><span data-stu-id="1f399-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1f399-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="1f399-149">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-149">win:UnicodeString</span></span>|<span data-ttu-id="1f399-150">Podpis spravované spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="1f399-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1f399-151">NativeMethodSignature</span></span>|<span data-ttu-id="1f399-152">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-152">win:UnicodeString</span></span>|<span data-ttu-id="1f399-153">Nativní metoda podpis.</span><span class="sxs-lookup"><span data-stu-id="1f399-153">The native method signature.</span></span>|  
|<span data-ttu-id="1f399-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1f399-154">StubMethodSignature</span></span>|<span data-ttu-id="1f399-155">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-155">win:UnicodeString</span></span>|<span data-ttu-id="1f399-156">Podpis metody se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="1f399-156">The stub method signature.</span></span>|  
|<span data-ttu-id="1f399-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="1f399-157">StubMethodILCode</span></span>|<span data-ttu-id="1f399-158">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-158">win:UnicodeString</span></span>|<span data-ttu-id="1f399-159">MSIL kód pro metodu se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="1f399-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="1f399-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1f399-160">ClrInstanceID</span></span>|<span data-ttu-id="1f399-161">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1f399-161">win:UInt16</span></span>|<span data-ttu-id="1f399-162">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1f399-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="1f399-163">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="1f399-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="1f399-164">ILStubCacheHit událostí</span><span class="sxs-lookup"><span data-stu-id="1f399-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="1f399-165">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="1f399-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1f399-166">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="1f399-166">Keyword for raising the event</span></span>|<span data-ttu-id="1f399-167">úroveň</span><span class="sxs-lookup"><span data-stu-id="1f399-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1f399-168">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="1f399-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="1f399-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="1f399-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="1f399-170">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="1f399-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1f399-171">Událost</span><span class="sxs-lookup"><span data-stu-id="1f399-171">Event</span></span>|<span data-ttu-id="1f399-172">ID události</span><span class="sxs-lookup"><span data-stu-id="1f399-172">Event ID</span></span>|<span data-ttu-id="1f399-173">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="1f399-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="1f399-174">89</span><span class="sxs-lookup"><span data-stu-id="1f399-174">89</span></span>|<span data-ttu-id="1f399-175">Přistupoval MSIL mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1f399-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="1f399-176">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="1f399-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1f399-177">Název pole</span><span class="sxs-lookup"><span data-stu-id="1f399-177">Field name</span></span>|<span data-ttu-id="1f399-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="1f399-178">Data type</span></span>|<span data-ttu-id="1f399-179">Popis</span><span class="sxs-lookup"><span data-stu-id="1f399-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1f399-180">ID modulu</span><span class="sxs-lookup"><span data-stu-id="1f399-180">ModuleID</span></span>|<span data-ttu-id="1f399-181">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1f399-181">win:UInt16</span></span>|<span data-ttu-id="1f399-182">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="1f399-182">The module identifier.</span></span>|  
|<span data-ttu-id="1f399-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="1f399-183">StubMethodID</span></span>|<span data-ttu-id="1f399-184">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="1f399-184">win:UInt64</span></span>|<span data-ttu-id="1f399-185">Identifikátor se zakázaným inzerováním metoda.</span><span class="sxs-lookup"><span data-stu-id="1f399-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="1f399-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="1f399-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="1f399-187">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1f399-187">win:UInt32</span></span>|<span data-ttu-id="1f399-188">Token pro metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1f399-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="1f399-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="1f399-190">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-190">win:UnicodeString</span></span>|<span data-ttu-id="1f399-191">Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="1f399-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="1f399-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="1f399-193">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-193">win:UnicodeString</span></span>|<span data-ttu-id="1f399-194">Název spravovaného zprostředkovatele komunikace s objekty metody.</span><span class="sxs-lookup"><span data-stu-id="1f399-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1f399-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="1f399-196">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1f399-196">win:UnicodeString</span></span>|<span data-ttu-id="1f399-197">Podpis spravované spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="1f399-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="1f399-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1f399-198">ClrInstanceID</span></span>|<span data-ttu-id="1f399-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1f399-199">win:UInt16</span></span>|<span data-ttu-id="1f399-200">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1f399-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="1f399-201">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="1f399-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="1f399-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f399-202">See Also</span></span>  
 [<span data-ttu-id="1f399-203">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="1f399-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
