---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124334"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="f97f7-102">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="f97f7-102">Debugging Enumerations</span></span>
<span data-ttu-id="f97f7-103">Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f97f7-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f97f7-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f97f7-104">In This Section</span></span>  
 [<span data-ttu-id="f97f7-105">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="f97f7-106">Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="f97f7-107">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="f97f7-108">Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="f97f7-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="f97f7-109">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="f97f7-110">Určuje typ procesu, který se má vyčíslit.</span><span class="sxs-lookup"><span data-stu-id="f97f7-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="f97f7-111">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="f97f7-112">Určuje důvody, proč se vlákno může v daném objektu zablokovat.</span><span class="sxs-lookup"><span data-stu-id="f97f7-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="f97f7-113">CorDebugChainReason –</span><span class="sxs-lookup"><span data-stu-id="f97f7-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="f97f7-114">Určuje důvod nebo důvody pro zahájení řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="f97f7-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="f97f7-115">CorDebugCodeInvokeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="f97f7-116">Popisuje, jak exportovaný funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f97f7-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="f97f7-117">CorDebugCodeInvokePurpose – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="f97f7-118">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f97f7-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="f97f7-119">CorDebugCreateProcessFlags –</span><span class="sxs-lookup"><span data-stu-id="f97f7-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="f97f7-120">Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="f97f7-121">CorDebugDebugEventKind – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="f97f7-122">Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="f97f7-123">CorDebugDecodeEventFlagsWindows – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="f97f7-124">Poskytuje další informace o událostech ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="f97f7-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="f97f7-125">CorDebugExceptionCallbackType –</span><span class="sxs-lookup"><span data-stu-id="f97f7-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="f97f7-126">Určuje typ zpětného volání, které je provedeno z události [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="f97f7-127">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="f97f7-128">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="f97f7-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="f97f7-129">CorDebugExceptionUnwindCallbackType –</span><span class="sxs-lookup"><span data-stu-id="f97f7-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="f97f7-130">Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f97f7-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="f97f7-131">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="f97f7-132">Označuje, zda systém uvolňování paměti běží na pracovní stanici nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="f97f7-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="f97f7-133">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="f97f7-134">Určuje generaci oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="f97f7-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="f97f7-135">CorDebugHandleType –</span><span class="sxs-lookup"><span data-stu-id="f97f7-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="f97f7-136">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="f97f7-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="f97f7-137">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="f97f7-138">Označuje, zda určitý rozsah nativních instrukcí odpovídá zvláštnímu regionu kódu.</span><span class="sxs-lookup"><span data-stu-id="f97f7-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="f97f7-139">CorDebugIntercept –</span><span class="sxs-lookup"><span data-stu-id="f97f7-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="f97f7-140">Určuje typy kódu, které mohou být na začátku.</span><span class="sxs-lookup"><span data-stu-id="f97f7-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="f97f7-141">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="f97f7-142">Určuje buď verzi .NET Framework, nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.</span><span class="sxs-lookup"><span data-stu-id="f97f7-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="f97f7-143">CorDebugInternalFrameType –</span><span class="sxs-lookup"><span data-stu-id="f97f7-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="f97f7-144">Určuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f97f7-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="f97f7-145">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="f97f7-146">Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="f97f7-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="f97f7-147">CorDebugJITCompilerFlagsDeprecated – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="f97f7-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f97f7-148">Obsolete.</span></span> <span data-ttu-id="f97f7-149">Místo toho použijte `CORDEBUG_JIT_DEFAULT` člen výčtu [CorDebugJITCompilerFlags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="f97f7-150">CorDebugMappingResult –</span><span class="sxs-lookup"><span data-stu-id="f97f7-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="f97f7-151">Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="f97f7-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="f97f7-152">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="f97f7-153">Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="f97f7-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="f97f7-154">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="f97f7-155">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="f97f7-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="f97f7-156">CorDebugPlatform – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="f97f7-157">Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f97f7-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="f97f7-158">CorDebugRecordFormat – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="f97f7-159">Popisuje formát dat v bajtovém poli, které obsahuje informace o nativní události ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="f97f7-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="f97f7-160">CorDebugRegister –</span><span class="sxs-lookup"><span data-stu-id="f97f7-160">CorDebugRegister</span></span>  
 <span data-ttu-id="f97f7-161">Určuje Registry přidružené k dané architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="f97f7-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="f97f7-162">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="f97f7-163">Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="f97f7-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="f97f7-164">CorDebugStateChange – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="f97f7-165">Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.</span><span class="sxs-lookup"><span data-stu-id="f97f7-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="f97f7-166">CorDebugStepReason –</span><span class="sxs-lookup"><span data-stu-id="f97f7-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="f97f7-167">Označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="f97f7-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="f97f7-168">CorDebugThreadState –</span><span class="sxs-lookup"><span data-stu-id="f97f7-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="f97f7-169">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f97f7-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="f97f7-170">\>CorDebugUnmappedStop –</span><span class="sxs-lookup"><span data-stu-id="f97f7-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="f97f7-171">Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.</span><span class="sxs-lookup"><span data-stu-id="f97f7-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="f97f7-172">CorDebugUserState –</span><span class="sxs-lookup"><span data-stu-id="f97f7-172">CorDebugUserState</span></span>  
 <span data-ttu-id="f97f7-173">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="f97f7-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="f97f7-174">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="f97f7-175">Určuje zdroj objektu, který má být shromážděn do paměti.</span><span class="sxs-lookup"><span data-stu-id="f97f7-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="f97f7-176">ILCodeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="f97f7-177">Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="f97f7-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="f97f7-178">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="f97f7-179">Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.</span><span class="sxs-lookup"><span data-stu-id="f97f7-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="f97f7-180">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="f97f7-181">Určuje operaci, která byla provedena na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="f97f7-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="f97f7-182">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="f97f7-183">Označuje typ nativního umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="f97f7-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="f97f7-184">WriteableMetadataUpdateMode – výčet</span><span class="sxs-lookup"><span data-stu-id="f97f7-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="f97f7-185">Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="f97f7-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="f97f7-186">[Výčet ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Poskytuje hodnoty, které jsou používány strukturou CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="f97f7-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f97f7-187">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f97f7-187">Related Sections</span></span>  
 [<span data-ttu-id="f97f7-188">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="f97f7-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="f97f7-189">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f97f7-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="f97f7-190">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="f97f7-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="f97f7-191">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="f97f7-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
