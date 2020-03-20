---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179144"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="04e0b-102">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="04e0b-102">Debugging Enumerations</span></span>
<span data-ttu-id="04e0b-103">Tato část popisuje nespravované výčty, které používá ladění rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="04e0b-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="04e0b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="04e0b-104">In This Section</span></span>  
 [<span data-ttu-id="04e0b-105">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="04e0b-106">Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging::OpenVirtualProcess.](iclrdebugging-openvirtualprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="04e0b-107">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="04e0b-108">Označuje, které oblasti paměti by mělo být zahrnuto do oblastí volání metody [ICLRDataEnumMemoryRegions::EnumMemoryRegions.](iclrdataenummemoryregions-enummemoryregions-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="04e0b-109">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="04e0b-110">Určuje typ procesu, který má být uveden ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="04e0b-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="04e0b-111">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="04e0b-112">Určuje důvody, proč může být vlákno blokováno na daném objektu.</span><span class="sxs-lookup"><span data-stu-id="04e0b-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="04e0b-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="04e0b-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="04e0b-114">Označuje důvod nebo důvody pro zahájení řetězce volání.</span><span class="sxs-lookup"><span data-stu-id="04e0b-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="04e0b-115">Výčet CorDebugCodeInvokeKind</span><span class="sxs-lookup"><span data-stu-id="04e0b-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="04e0b-116">Popisuje, jak exportovaná funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="04e0b-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="04e0b-117">CorDebugCodeInvokePurpose – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="04e0b-118">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="04e0b-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="04e0b-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="04e0b-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="04e0b-120">Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug::CreateProcess.](icordebug-createprocess-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="04e0b-121">CorDebugDebugEventKind – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="04e0b-122">Označuje typ události, jejíž informace jsou dekódovány metodou [DecodeEvent.](icordebugprocess6-decodeevent-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="04e0b-123">Výčet CorDebugDecodeEventFlagsWindows</span><span class="sxs-lookup"><span data-stu-id="04e0b-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="04e0b-124">Obsahuje další informace o ladicích událostech na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="04e0b-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="04e0b-125">Typ příkazu CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="04e0b-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="04e0b-126">Označuje typ zpětného volání, který je vyroben z [Události ICorDebugManagedCallback2::Exception.](icordebugmanagedcallback2-exception-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="04e0b-127">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="04e0b-128">Obsahuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="04e0b-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="04e0b-129">CorDebugExceptionUnwindbackType</span><span class="sxs-lookup"><span data-stu-id="04e0b-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="04e0b-130">Označuje událost, která je signalizována zpětného volání během fáze unwind.</span><span class="sxs-lookup"><span data-stu-id="04e0b-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="04e0b-131">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="04e0b-132">Označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="04e0b-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="04e0b-133">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="04e0b-134">Určuje generování oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="04e0b-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="04e0b-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="04e0b-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="04e0b-136">Označuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="04e0b-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="04e0b-137">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="04e0b-138">Označuje, zda určitý rozsah nativní pokyny odpovídá zvláštní kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="04e0b-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="04e0b-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="04e0b-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="04e0b-140">Označuje typy kódu, do kterého lze zasílat.</span><span class="sxs-lookup"><span data-stu-id="04e0b-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="04e0b-141">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="04e0b-142">Určuje verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve které bylo zavedeno rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04e0b-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="04e0b-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="04e0b-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="04e0b-144">Identifikuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="04e0b-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="04e0b-145">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="04e0b-146">Obsahuje hodnoty, které ovlivňují chování spravovaného kompilátoru just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="04e0b-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="04e0b-147">CorDebugJITCompilerFlagsDeprecated – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="04e0b-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="04e0b-148">Obsolete.</span></span> <span data-ttu-id="04e0b-149">Použijte `CORDEBUG_JIT_DEFAULT` člen [corDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) výčtu místo.</span><span class="sxs-lookup"><span data-stu-id="04e0b-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="04e0b-150">Výsledek mapování cordebug</span><span class="sxs-lookup"><span data-stu-id="04e0b-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="04e0b-151">Obsahuje podrobnosti o tom, jak byla získána hodnota ukazatele instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="04e0b-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="04e0b-152">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="04e0b-153">Určuje stav vlákna, na kterém je aktivován aditovaný pomocník pro ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="04e0b-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="04e0b-154">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="04e0b-155">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní (NGen) obrazy z nativní mezipaměti bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="04e0b-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="04e0b-156">Výčet CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="04e0b-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="04e0b-157">Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget::GetPlatform.](icordebugdatatarget-getplatform-method.md)</span><span class="sxs-lookup"><span data-stu-id="04e0b-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="04e0b-158">Výčet CorDebugRecordFormat</span><span class="sxs-lookup"><span data-stu-id="04e0b-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="04e0b-159">Popisuje formát dat v bajtovém poli, které obsahuje informace o události ladění nativní výjimky.</span><span class="sxs-lookup"><span data-stu-id="04e0b-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="04e0b-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="04e0b-160">CorDebugRegister</span></span>  
 <span data-ttu-id="04e0b-161">Určuje registry přidružené k dané architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="04e0b-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="04e0b-162">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="04e0b-163">Označuje, zda je kontext z aktivního (nebo listového) rámce v zásobníku nebo byl vypočítán odvíjením z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="04e0b-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="04e0b-164">CorDebugStateChange – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="04e0b-165">Popisuje množství dat uložených v mezipaměti, která musí být zahozena na základě změn procesu.</span><span class="sxs-lookup"><span data-stu-id="04e0b-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="04e0b-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="04e0b-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="04e0b-167">Označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="04e0b-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="04e0b-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="04e0b-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="04e0b-169">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="04e0b-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="04e0b-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="04e0b-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="04e0b-171">Určuje typ nenamapovaného kódu, který může spustit zastavení provádění kódu krokovačem.</span><span class="sxs-lookup"><span data-stu-id="04e0b-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="04e0b-172">Stav uživatele cordebug</span><span class="sxs-lookup"><span data-stu-id="04e0b-172">CorDebugUserState</span></span>  
 <span data-ttu-id="04e0b-173">Označuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="04e0b-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="04e0b-174">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="04e0b-175">Identifikuje zdroj objektu, který má být uvolněn.</span><span class="sxs-lookup"><span data-stu-id="04e0b-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="04e0b-176">ILCodeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="04e0b-177">Poskytuje hodnoty, které určují, zda ladicí program je schopen přistupovat k místním proměnným nebo kódu přidanému v instrumentaci ReJIT profileru.</span><span class="sxs-lookup"><span data-stu-id="04e0b-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="04e0b-178">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="04e0b-179">Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.</span><span class="sxs-lookup"><span data-stu-id="04e0b-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="04e0b-180">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="04e0b-181">Označuje operaci, která byla provedena na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="04e0b-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="04e0b-182">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="04e0b-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="04e0b-183">Označuje nativní typ umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="04e0b-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="04e0b-184">Výčet WriteableMetadataUpdateMode</span><span class="sxs-lookup"><span data-stu-id="04e0b-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="04e0b-185">Poskytuje hodnoty, které určují, zda jsou aktualizace metadat v paměti viditelné pro ladicí program.</span><span class="sxs-lookup"><span data-stu-id="04e0b-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="04e0b-186">[Výčet clrDataSourceType](clrdatasourcetype-enumeration.md) Obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.</span><span class="sxs-lookup"><span data-stu-id="04e0b-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="04e0b-187">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="04e0b-187">Related Sections</span></span>  
 [<span data-ttu-id="04e0b-188">Ladění tříd typu coclass</span><span class="sxs-lookup"><span data-stu-id="04e0b-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="04e0b-189">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04e0b-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="04e0b-190">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="04e0b-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="04e0b-191">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="04e0b-191">Debugging Structures</span></span>](debugging-structures.md)
