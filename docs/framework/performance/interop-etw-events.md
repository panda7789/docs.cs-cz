---
title: Události Trasování událostí pro Windows interoperability
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949302"
---
# <a name="interop-etw-events"></a><span data-ttu-id="81a8d-102">Události Trasování událostí pro Windows interoperability</span><span class="sxs-lookup"><span data-stu-id="81a8d-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="81a8d-103">Události interoperability zaznamenat informace o Microsoft intermediate language (MSIL) zástupné procedury generování a ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="81a8d-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="81a8d-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="81a8d-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="81a8d-105">ILStubGenerated události</span><span class="sxs-lookup"><span data-stu-id="81a8d-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="81a8d-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="81a8d-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="81a8d-107">ILStubGenerated události</span><span class="sxs-lookup"><span data-stu-id="81a8d-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="81a8d-108">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="81a8d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="81a8d-109">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="81a8d-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="81a8d-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="81a8d-110">Keyword for raising the event</span></span>|<span data-ttu-id="81a8d-111">úroveň</span><span class="sxs-lookup"><span data-stu-id="81a8d-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="81a8d-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="81a8d-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="81a8d-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="81a8d-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="81a8d-114">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="81a8d-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="81a8d-115">Událost</span><span class="sxs-lookup"><span data-stu-id="81a8d-115">Event</span></span>|<span data-ttu-id="81a8d-116">ID události</span><span class="sxs-lookup"><span data-stu-id="81a8d-116">Event ID</span></span>|<span data-ttu-id="81a8d-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="81a8d-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="81a8d-118">88</span><span class="sxs-lookup"><span data-stu-id="81a8d-118">88</span></span>|<span data-ttu-id="81a8d-119">Byl vytvořen testovací kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="81a8d-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="81a8d-120">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="81a8d-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="81a8d-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="81a8d-121">Field name</span></span>|<span data-ttu-id="81a8d-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="81a8d-122">Data type</span></span>|<span data-ttu-id="81a8d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="81a8d-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="81a8d-124">ID modulu</span><span class="sxs-lookup"><span data-stu-id="81a8d-124">ModuleID</span></span>|<span data-ttu-id="81a8d-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="81a8d-125">win:UInt16</span></span>|<span data-ttu-id="81a8d-126">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-126">The module identifier.</span></span>|  
|<span data-ttu-id="81a8d-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="81a8d-127">StubMethodID</span></span>|<span data-ttu-id="81a8d-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="81a8d-128">win:UInt64</span></span>|<span data-ttu-id="81a8d-129">Metoda identifikátor zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="81a8d-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="81a8d-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="81a8d-130">StubFlags</span></span>|<span data-ttu-id="81a8d-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="81a8d-131">win:UInt64</span></span>|<span data-ttu-id="81a8d-132">Příznaky pro zástupná procedura:</span><span class="sxs-lookup"><span data-stu-id="81a8d-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="81a8d-133">0x1 – reverzní zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="81a8d-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="81a8d-134">0x2 - komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="81a8d-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="81a8d-135">0x4 - zástupné proceduře vygenerované pomocí NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="81a8d-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="81a8d-136">0x8 - delegáta.</span><span class="sxs-lookup"><span data-stu-id="81a8d-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="81a8d-137">0x10 - arrgument proměnné.</span><span class="sxs-lookup"><span data-stu-id="81a8d-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="81a8d-138">0x20 – nespravované volaný.</span><span class="sxs-lookup"><span data-stu-id="81a8d-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="81a8d-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="81a8d-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="81a8d-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="81a8d-140">win:UInt32</span></span>|<span data-ttu-id="81a8d-141">Token pro spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="81a8d-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="81a8d-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-143">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-144">Obor názvů spravovaná metoda spolupráce.</span><span class="sxs-lookup"><span data-stu-id="81a8d-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="81a8d-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="81a8d-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-146">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-147">Název spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="81a8d-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="81a8d-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-149">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-150">Podpis spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="81a8d-151">NativeMethodSignature</span></span>|<span data-ttu-id="81a8d-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-152">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-153">Nativní metoda podpis.</span><span class="sxs-lookup"><span data-stu-id="81a8d-153">The native method signature.</span></span>|  
|<span data-ttu-id="81a8d-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="81a8d-154">StubMethodSignature</span></span>|<span data-ttu-id="81a8d-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-155">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-156">Podpis metody zástupných procedur.</span><span class="sxs-lookup"><span data-stu-id="81a8d-156">The stub method signature.</span></span>|  
|<span data-ttu-id="81a8d-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="81a8d-157">StubMethodILCode</span></span>|<span data-ttu-id="81a8d-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-158">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-159">Kód jazyka MSIL pro metody zástupných procedur.</span><span class="sxs-lookup"><span data-stu-id="81a8d-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="81a8d-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="81a8d-160">ClrInstanceID</span></span>|<span data-ttu-id="81a8d-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="81a8d-161">win:UInt16</span></span>|<span data-ttu-id="81a8d-162">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="81a8d-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="81a8d-163">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="81a8d-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="81a8d-164">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="81a8d-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="81a8d-165">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="81a8d-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="81a8d-166">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="81a8d-166">Keyword for raising the event</span></span>|<span data-ttu-id="81a8d-167">úroveň</span><span class="sxs-lookup"><span data-stu-id="81a8d-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="81a8d-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="81a8d-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="81a8d-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="81a8d-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="81a8d-170">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="81a8d-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="81a8d-171">Událost</span><span class="sxs-lookup"><span data-stu-id="81a8d-171">Event</span></span>|<span data-ttu-id="81a8d-172">ID události</span><span class="sxs-lookup"><span data-stu-id="81a8d-172">Event ID</span></span>|<span data-ttu-id="81a8d-173">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="81a8d-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="81a8d-174">89</span><span class="sxs-lookup"><span data-stu-id="81a8d-174">89</span></span>|<span data-ttu-id="81a8d-175">Jazyk MSIL mezipaměti byl otevřen.</span><span class="sxs-lookup"><span data-stu-id="81a8d-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="81a8d-176">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="81a8d-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="81a8d-177">Název pole</span><span class="sxs-lookup"><span data-stu-id="81a8d-177">Field name</span></span>|<span data-ttu-id="81a8d-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="81a8d-178">Data type</span></span>|<span data-ttu-id="81a8d-179">Popis</span><span class="sxs-lookup"><span data-stu-id="81a8d-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="81a8d-180">ID modulu</span><span class="sxs-lookup"><span data-stu-id="81a8d-180">ModuleID</span></span>|<span data-ttu-id="81a8d-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="81a8d-181">win:UInt16</span></span>|<span data-ttu-id="81a8d-182">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="81a8d-182">The module identifier.</span></span>|  
|<span data-ttu-id="81a8d-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="81a8d-183">StubMethodID</span></span>|<span data-ttu-id="81a8d-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="81a8d-184">win:UInt64</span></span>|<span data-ttu-id="81a8d-185">Metoda identifikátor zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="81a8d-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="81a8d-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="81a8d-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="81a8d-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="81a8d-187">win:UInt32</span></span>|<span data-ttu-id="81a8d-188">Token pro spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="81a8d-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="81a8d-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-190">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-191">Obor názvů spravovaná metoda spolupráce.</span><span class="sxs-lookup"><span data-stu-id="81a8d-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="81a8d-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="81a8d-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-193">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-194">Název spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="81a8d-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="81a8d-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="81a8d-196">win:UnicodeString</span></span>|<span data-ttu-id="81a8d-197">Podpis spravované vzájemné spolupráce metody.</span><span class="sxs-lookup"><span data-stu-id="81a8d-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="81a8d-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="81a8d-198">ClrInstanceID</span></span>|<span data-ttu-id="81a8d-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="81a8d-199">win:UInt16</span></span>|<span data-ttu-id="81a8d-200">Jedinečné ID instance CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="81a8d-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="81a8d-201">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="81a8d-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="81a8d-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81a8d-202">See also</span></span>

- [<span data-ttu-id="81a8d-203">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="81a8d-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
