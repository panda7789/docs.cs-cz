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
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="b3cb1-102">Události Trasování událostí pro Windows interoperability</span><span class="sxs-lookup"><span data-stu-id="b3cb1-102">Interop ETW Events</span></span>
<a name="top"></a><span data-ttu-id="b3cb1-103">Události interoperability zaznamenat informace o Microsoft (MSIL intermediate language) se zakázaným inzerováním generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="b3cb1-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="b3cb1-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="b3cb1-105">ILStubGenerated událostí</span><span class="sxs-lookup"><span data-stu-id="b3cb1-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="b3cb1-106">ILStubCacheHit událostí</span><span class="sxs-lookup"><span data-stu-id="b3cb1-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="b3cb1-107">ILStubGenerated událostí</span><span class="sxs-lookup"><span data-stu-id="b3cb1-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="b3cb1-108">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="b3cb1-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="b3cb1-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b3cb1-110">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b3cb1-110">Keyword for raising the event</span></span>|<span data-ttu-id="b3cb1-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="b3cb1-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b3cb1-112">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="b3cb1-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="b3cb1-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="b3cb1-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="b3cb1-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b3cb1-115">Událost</span><span class="sxs-lookup"><span data-stu-id="b3cb1-115">Event</span></span>|<span data-ttu-id="b3cb1-116">ID události</span><span class="sxs-lookup"><span data-stu-id="b3cb1-116">Event ID</span></span>|<span data-ttu-id="b3cb1-117">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="b3cb1-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="b3cb1-118">88</span><span class="sxs-lookup"><span data-stu-id="b3cb1-118">88</span></span>|<span data-ttu-id="b3cb1-119">MSIL stub byla vygenerována.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="b3cb1-120">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b3cb1-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="b3cb1-121">Field name</span></span>|<span data-ttu-id="b3cb1-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3cb1-122">Data type</span></span>|<span data-ttu-id="b3cb1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b3cb1-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b3cb1-124">ID modulu</span><span class="sxs-lookup"><span data-stu-id="b3cb1-124">ModuleID</span></span>|<span data-ttu-id="b3cb1-125">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b3cb1-125">win:UInt16</span></span>|<span data-ttu-id="b3cb1-126">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-126">The module identifier.</span></span>|  
|<span data-ttu-id="b3cb1-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="b3cb1-127">StubMethodID</span></span>|<span data-ttu-id="b3cb1-128">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b3cb1-128">win:UInt64</span></span>|<span data-ttu-id="b3cb1-129">Identifikátor se zakázaným inzerováním metoda.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="b3cb1-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="b3cb1-130">StubFlags</span></span>|<span data-ttu-id="b3cb1-131">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b3cb1-131">win:UInt64</span></span>|<span data-ttu-id="b3cb1-132">Příznaky pro testovací kód:</span><span class="sxs-lookup"><span data-stu-id="b3cb1-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="b3cb1-133">0x1 - zpětné zprostředkovatel komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="b3cb1-134">0x2 - zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="b3cb1-135">0x4 - stub generované NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="b3cb1-136">0x8 - delegáta.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="b3cb1-137">0x10 - proměnné arrgument.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="b3cb1-138">0x20 – nespravované volaný.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="b3cb1-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="b3cb1-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="b3cb1-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b3cb1-140">win:UInt32</span></span>|<span data-ttu-id="b3cb1-141">Token pro metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="b3cb1-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="b3cb1-143">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-143">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-144">Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="b3cb1-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="b3cb1-146">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-146">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-147">Název spravovaného zprostředkovatele komunikace s objekty metody.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b3cb1-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="b3cb1-149">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-149">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-150">Podpis spravované spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b3cb1-151">NativeMethodSignature</span></span>|<span data-ttu-id="b3cb1-152">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-152">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-153">Nativní metoda podpis.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-153">The native method signature.</span></span>|  
|<span data-ttu-id="b3cb1-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b3cb1-154">StubMethodSignature</span></span>|<span data-ttu-id="b3cb1-155">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-155">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-156">Podpis metody se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-156">The stub method signature.</span></span>|  
|<span data-ttu-id="b3cb1-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="b3cb1-157">StubMethodILCode</span></span>|<span data-ttu-id="b3cb1-158">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-158">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-159">MSIL kód pro metodu se zakázaným inzerováním.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="b3cb1-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b3cb1-160">ClrInstanceID</span></span>|<span data-ttu-id="b3cb1-161">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b3cb1-161">win:UInt16</span></span>|<span data-ttu-id="b3cb1-162">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b3cb1-163">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="b3cb1-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="b3cb1-164">ILStubCacheHit událostí</span><span class="sxs-lookup"><span data-stu-id="b3cb1-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="b3cb1-165">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b3cb1-166">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="b3cb1-166">Keyword for raising the event</span></span>|<span data-ttu-id="b3cb1-167">úroveň</span><span class="sxs-lookup"><span data-stu-id="b3cb1-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b3cb1-168">`InteropKeyword`(0x2000)</span><span class="sxs-lookup"><span data-stu-id="b3cb1-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="b3cb1-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="b3cb1-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="b3cb1-170">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b3cb1-171">Událost</span><span class="sxs-lookup"><span data-stu-id="b3cb1-171">Event</span></span>|<span data-ttu-id="b3cb1-172">ID události</span><span class="sxs-lookup"><span data-stu-id="b3cb1-172">Event ID</span></span>|<span data-ttu-id="b3cb1-173">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="b3cb1-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="b3cb1-174">89</span><span class="sxs-lookup"><span data-stu-id="b3cb1-174">89</span></span>|<span data-ttu-id="b3cb1-175">Přistupoval MSIL mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="b3cb1-176">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b3cb1-177">Název pole</span><span class="sxs-lookup"><span data-stu-id="b3cb1-177">Field name</span></span>|<span data-ttu-id="b3cb1-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3cb1-178">Data type</span></span>|<span data-ttu-id="b3cb1-179">Popis</span><span class="sxs-lookup"><span data-stu-id="b3cb1-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b3cb1-180">ID modulu</span><span class="sxs-lookup"><span data-stu-id="b3cb1-180">ModuleID</span></span>|<span data-ttu-id="b3cb1-181">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b3cb1-181">win:UInt16</span></span>|<span data-ttu-id="b3cb1-182">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-182">The module identifier.</span></span>|  
|<span data-ttu-id="b3cb1-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="b3cb1-183">StubMethodID</span></span>|<span data-ttu-id="b3cb1-184">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="b3cb1-184">win:UInt64</span></span>|<span data-ttu-id="b3cb1-185">Identifikátor se zakázaným inzerováním metoda.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="b3cb1-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="b3cb1-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="b3cb1-187">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b3cb1-187">win:UInt32</span></span>|<span data-ttu-id="b3cb1-188">Token pro metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="b3cb1-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="b3cb1-190">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-190">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-191">Obor názvů metodu spravovaného zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="b3cb1-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="b3cb1-193">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-193">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-194">Název spravovaného zprostředkovatele komunikace s objekty metody.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b3cb1-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="b3cb1-196">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b3cb1-196">win:UnicodeString</span></span>|<span data-ttu-id="b3cb1-197">Podpis spravované spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="b3cb1-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b3cb1-198">ClrInstanceID</span></span>|<span data-ttu-id="b3cb1-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b3cb1-199">win:UInt16</span></span>|<span data-ttu-id="b3cb1-200">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b3cb1-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b3cb1-201">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="b3cb1-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="b3cb1-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3cb1-202">See Also</span></span>  
 [<span data-ttu-id="b3cb1-203">CLR ETW – události</span><span class="sxs-lookup"><span data-stu-id="b3cb1-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
