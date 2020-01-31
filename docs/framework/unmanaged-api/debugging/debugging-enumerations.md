---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789158"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="89408-102">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="89408-102">Debugging Enumerations</span></span>
<span data-ttu-id="89408-103">Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="89408-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89408-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="89408-104">In This Section</span></span>  
 [<span data-ttu-id="89408-105">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="89408-106">Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="89408-107">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="89408-108">Určuje, které oblasti paměti musí volání metody [ICLRDataEnumMemoryRegions –:: EnumMemoryRegions –](iclrdataenummemoryregions-enummemoryregions-method.md) zahrnovat.</span><span class="sxs-lookup"><span data-stu-id="89408-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="89408-109">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="89408-110">Určuje typ procesu, který se má vyčíslit.</span><span class="sxs-lookup"><span data-stu-id="89408-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="89408-111">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="89408-112">Určuje důvody, proč se vlákno může v daném objektu zablokovat.</span><span class="sxs-lookup"><span data-stu-id="89408-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="89408-113">CorDebugChainReason –</span><span class="sxs-lookup"><span data-stu-id="89408-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="89408-114">Určuje důvod nebo důvody pro zahájení řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="89408-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="89408-115">CorDebugCodeInvokeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="89408-116">Popisuje, jak exportovaný funkce vyvolá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="89408-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="89408-117">CorDebugCodeInvokePurpose – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="89408-118">Popisuje, proč exportovaná funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="89408-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="89408-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="89408-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="89408-120">Poskytuje další možnosti ladění, které lze použít při volání metody [ICorDebug:: CreateProcess](icordebug-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="89408-121">CorDebugDebugEventKind – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="89408-122">Určuje typ události, jejíž informace je dekódovat metodou [DecodeEvent –](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="89408-123">CorDebugDecodeEventFlagsWindows – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="89408-124">Poskytuje další informace o událostech ladění na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="89408-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="89408-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="89408-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="89408-126">Určuje typ zpětného volání, které je provedeno z události [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="89408-127">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="89408-128">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="89408-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="89408-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="89408-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="89408-130">Určuje událost, která je během fáze unwind signalizována signálem zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="89408-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="89408-131">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="89408-132">Označuje, zda systém uvolňování paměti běží na pracovní stanici nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="89408-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="89408-133">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="89408-134">Určuje generaci oblasti paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="89408-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="89408-135">CorDebugHandleType –</span><span class="sxs-lookup"><span data-stu-id="89408-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="89408-136">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="89408-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="89408-137">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="89408-138">Označuje, zda určitý rozsah nativních instrukcí odpovídá zvláštnímu regionu kódu.</span><span class="sxs-lookup"><span data-stu-id="89408-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="89408-139">CorDebugIntercept –</span><span class="sxs-lookup"><span data-stu-id="89408-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="89408-140">Určuje typy kódu, které mohou být na začátku.</span><span class="sxs-lookup"><span data-stu-id="89408-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="89408-141">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="89408-142">Určuje buď verzi .NET Framework, nebo verzi .NET Framework, ve které bylo rozhraní zavedeno.</span><span class="sxs-lookup"><span data-stu-id="89408-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="89408-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="89408-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="89408-144">Určuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="89408-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="89408-145">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="89408-146">Obsahuje hodnoty, které mají vliv na chování spravovaného kompilátoru JIT (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="89408-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="89408-147">CorDebugJITCompilerFlagsDeprecated – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="89408-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="89408-148">Obsolete.</span></span> <span data-ttu-id="89408-149">Místo toho použijte `CORDEBUG_JIT_DEFAULT` člen výčtu [CorDebugJITCompilerFlags –](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="89408-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="89408-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="89408-151">Poskytuje podrobné informace o tom, jak byla získána hodnota ukazatele na instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="89408-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="89408-152">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="89408-153">Určuje stav vlákna, ve kterém je aktivován pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="89408-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="89408-154">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="89408-155">Poskytuje hodnotu, která určuje, zda ladicí program načte nativní bitové kopie (NGen) z mezipaměti nativních imagí.</span><span class="sxs-lookup"><span data-stu-id="89408-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="89408-156">CorDebugPlatform – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="89408-157">Poskytuje hodnoty cílové platformy, které jsou používány metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89408-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="89408-158">CorDebugRecordFormat – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="89408-159">Popisuje formát dat v bajtovém poli, které obsahuje informace o nativní události ladění výjimky.</span><span class="sxs-lookup"><span data-stu-id="89408-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="89408-160">CorDebugRegister –</span><span class="sxs-lookup"><span data-stu-id="89408-160">CorDebugRegister</span></span>  
 <span data-ttu-id="89408-161">Určuje Registry přidružené k dané architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="89408-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="89408-162">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="89408-163">Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="89408-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="89408-164">CorDebugStateChange – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="89408-165">Popisuje množství dat uložených v mezipaměti, které je nutné zahodit na základě změn procesu.</span><span class="sxs-lookup"><span data-stu-id="89408-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="89408-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="89408-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="89408-167">Označuje výsledek jednotlivého kroku.</span><span class="sxs-lookup"><span data-stu-id="89408-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="89408-168">CorDebugThreadState –</span><span class="sxs-lookup"><span data-stu-id="89408-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="89408-169">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="89408-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="89408-170">\>CorDebugUnmappedStop –</span><span class="sxs-lookup"><span data-stu-id="89408-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="89408-171">Určuje typ nemapovaného kódu, který může aktivovat zastavení při provádění kódu stepper.</span><span class="sxs-lookup"><span data-stu-id="89408-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="89408-172">CorDebugUserState –</span><span class="sxs-lookup"><span data-stu-id="89408-172">CorDebugUserState</span></span>  
 <span data-ttu-id="89408-173">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="89408-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="89408-174">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="89408-175">Určuje zdroj objektu, který má být shromážděn do paměti.</span><span class="sxs-lookup"><span data-stu-id="89408-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="89408-176">ILCodeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="89408-177">Poskytuje hodnoty, které určují, jestli má ladicí program přístup k místním proměnným nebo kódu přidanému v profileru ReJIT instrumentace.</span><span class="sxs-lookup"><span data-stu-id="89408-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="89408-178">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="89408-179">Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.</span><span class="sxs-lookup"><span data-stu-id="89408-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="89408-180">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="89408-181">Určuje operaci, která byla provedena na přepínači ladění/trasování.</span><span class="sxs-lookup"><span data-stu-id="89408-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="89408-182">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="89408-183">Označuje typ nativního umístění proměnné.</span><span class="sxs-lookup"><span data-stu-id="89408-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="89408-184">WriteableMetadataUpdateMode – výčet</span><span class="sxs-lookup"><span data-stu-id="89408-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="89408-185">Poskytuje hodnoty, které určují, zda mají být aktualizace metadat v paměti viditelné ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="89408-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="89408-186">[Výčet ClrDataSourceType](clrdatasourcetype-enumeration.md) Poskytuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP strukturou.</span><span class="sxs-lookup"><span data-stu-id="89408-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="89408-187">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="89408-187">Related Sections</span></span>  
 [<span data-ttu-id="89408-188">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="89408-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="89408-189">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="89408-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="89408-190">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="89408-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="89408-191">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="89408-191">Debugging Structures</span></span>](debugging-structures.md)
