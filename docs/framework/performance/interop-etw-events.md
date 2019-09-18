---
title: Události Trasování událostí pro Windows interoperability
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787c6221b651a53dbb932a5a9d0edea123e1d97d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046438"
---
# <a name="interop-etw-events"></a><span data-ttu-id="ec0a2-102">Události Trasování událostí pro Windows interoperability</span><span class="sxs-lookup"><span data-stu-id="ec0a2-102">Interop ETW Events</span></span>
<a name="top"></a><span data-ttu-id="ec0a2-103">Události vzájemné spolupráce zachytí informace o generování a ukládání procedury do mezipaměti v jazyce MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="ec0a2-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="ec0a2-104">Tato kategorie se skládá z následujících událostí:</span><span class="sxs-lookup"><span data-stu-id="ec0a2-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="ec0a2-105">Událost ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="ec0a2-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="ec0a2-106">ILStubCacheHit Event</span><span class="sxs-lookup"><span data-stu-id="ec0a2-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="ec0a2-107">Událost ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="ec0a2-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="ec0a2-108">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="ec0a2-109">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ec0a2-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ec0a2-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ec0a2-110">Keyword for raising the event</span></span>|<span data-ttu-id="ec0a2-111">Level</span><span class="sxs-lookup"><span data-stu-id="ec0a2-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ec0a2-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="ec0a2-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="ec0a2-113">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ec0a2-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="ec0a2-114">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ec0a2-115">Událost</span><span class="sxs-lookup"><span data-stu-id="ec0a2-115">Event</span></span>|<span data-ttu-id="ec0a2-116">ID události</span><span class="sxs-lookup"><span data-stu-id="ec0a2-116">Event ID</span></span>|<span data-ttu-id="ec0a2-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ec0a2-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="ec0a2-118">88</span><span class="sxs-lookup"><span data-stu-id="ec0a2-118">88</span></span>|<span data-ttu-id="ec0a2-119">Byl vygenerován zástupný kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="ec0a2-120">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ec0a2-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="ec0a2-121">Field name</span></span>|<span data-ttu-id="ec0a2-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ec0a2-122">Data type</span></span>|<span data-ttu-id="ec0a2-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ec0a2-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ec0a2-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-124">ModuleID</span></span>|<span data-ttu-id="ec0a2-125">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ec0a2-125">win:UInt16</span></span>|<span data-ttu-id="ec0a2-126">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-126">The module identifier.</span></span>|  
|<span data-ttu-id="ec0a2-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-127">StubMethodID</span></span>|<span data-ttu-id="ec0a2-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ec0a2-128">win:UInt64</span></span>|<span data-ttu-id="ec0a2-129">Identifikátor metody zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="ec0a2-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="ec0a2-130">StubFlags</span></span>|<span data-ttu-id="ec0a2-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ec0a2-131">win:UInt64</span></span>|<span data-ttu-id="ec0a2-132">Příznaky pro zástupnou proceduru:</span><span class="sxs-lookup"><span data-stu-id="ec0a2-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="ec0a2-133">0x1 – reverzní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="ec0a2-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="ec0a2-134">pře0x2-COM Interop.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="ec0a2-135">0x4 – zástupné procedury generované NGen. exe.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="ec0a2-136">0x8 – Delegate</span><span class="sxs-lookup"><span data-stu-id="ec0a2-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="ec0a2-137">Argument 0x10-Variable</span><span class="sxs-lookup"><span data-stu-id="ec0a2-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="ec0a2-138">0x20 – nespravovaný volaný</span><span class="sxs-lookup"><span data-stu-id="ec0a2-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="ec0a2-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="ec0a2-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="ec0a2-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ec0a2-140">win:UInt32</span></span>|<span data-ttu-id="ec0a2-141">Token pro spravovanou metodu spolupráce</span><span class="sxs-lookup"><span data-stu-id="ec0a2-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="ec0a2-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="ec0a2-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-143">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-144">Obor názvů spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="ec0a2-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="ec0a2-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-146">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-147">Název spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="ec0a2-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="ec0a2-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-149">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-150">Podpis spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="ec0a2-151">NativeMethodSignature</span></span>|<span data-ttu-id="ec0a2-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-152">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-153">Signatura nativní metody.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-153">The native method signature.</span></span>|  
|<span data-ttu-id="ec0a2-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="ec0a2-154">StubMethodSignature</span></span>|<span data-ttu-id="ec0a2-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-155">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-156">Podpis metody zástupné procedury</span><span class="sxs-lookup"><span data-stu-id="ec0a2-156">The stub method signature.</span></span>|  
|<span data-ttu-id="ec0a2-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="ec0a2-157">StubMethodILCode</span></span>|<span data-ttu-id="ec0a2-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-158">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-159">Kód jazyka MSIL pro metodu zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="ec0a2-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-160">ClrInstanceID</span></span>|<span data-ttu-id="ec0a2-161">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ec0a2-161">win:UInt16</span></span>|<span data-ttu-id="ec0a2-162">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ec0a2-163">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ec0a2-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="ec0a2-164">Událost ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="ec0a2-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="ec0a2-165">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="ec0a2-166">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="ec0a2-166">Keyword for raising the event</span></span>|<span data-ttu-id="ec0a2-167">Level</span><span class="sxs-lookup"><span data-stu-id="ec0a2-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ec0a2-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="ec0a2-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="ec0a2-169">Informační (4)</span><span class="sxs-lookup"><span data-stu-id="ec0a2-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="ec0a2-170">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ec0a2-171">Událost</span><span class="sxs-lookup"><span data-stu-id="ec0a2-171">Event</span></span>|<span data-ttu-id="ec0a2-172">ID události</span><span class="sxs-lookup"><span data-stu-id="ec0a2-172">Event ID</span></span>|<span data-ttu-id="ec0a2-173">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="ec0a2-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="ec0a2-174">89</span><span class="sxs-lookup"><span data-stu-id="ec0a2-174">89</span></span>|<span data-ttu-id="ec0a2-175">K mezipaměti MSIL bylo přistup.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="ec0a2-176">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ec0a2-177">Název pole</span><span class="sxs-lookup"><span data-stu-id="ec0a2-177">Field name</span></span>|<span data-ttu-id="ec0a2-178">Datový typ</span><span class="sxs-lookup"><span data-stu-id="ec0a2-178">Data type</span></span>|<span data-ttu-id="ec0a2-179">Popis</span><span class="sxs-lookup"><span data-stu-id="ec0a2-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ec0a2-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-180">ModuleID</span></span>|<span data-ttu-id="ec0a2-181">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ec0a2-181">win:UInt16</span></span>|<span data-ttu-id="ec0a2-182">Identifikátor modulu.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-182">The module identifier.</span></span>|  
|<span data-ttu-id="ec0a2-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-183">StubMethodID</span></span>|<span data-ttu-id="ec0a2-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="ec0a2-184">win:UInt64</span></span>|<span data-ttu-id="ec0a2-185">Identifikátor metody zástupné procedury.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="ec0a2-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="ec0a2-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="ec0a2-187">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="ec0a2-187">win:UInt32</span></span>|<span data-ttu-id="ec0a2-188">Token pro spravovanou metodu spolupráce</span><span class="sxs-lookup"><span data-stu-id="ec0a2-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="ec0a2-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="ec0a2-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-190">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-191">Obor názvů spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="ec0a2-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="ec0a2-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-193">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-194">Název spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="ec0a2-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="ec0a2-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ec0a2-196">win:UnicodeString</span></span>|<span data-ttu-id="ec0a2-197">Podpis spravované metody spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="ec0a2-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ec0a2-198">ClrInstanceID</span></span>|<span data-ttu-id="ec0a2-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="ec0a2-199">win:UInt16</span></span>|<span data-ttu-id="ec0a2-200">Jedinečné ID pro instanci CLR nebo CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ec0a2-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="ec0a2-201">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="ec0a2-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="ec0a2-202">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec0a2-202">See also</span></span>

- [<span data-ttu-id="ec0a2-203">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="ec0a2-203">CLR ETW Events</span></span>](clr-etw-events.md)
