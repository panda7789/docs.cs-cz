---
title: Ladění výčtů
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698509"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="ec60e-102">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="ec60e-102">Debugging Enumerations</span></span>
<span data-ttu-id="ec60e-103">Tato část popisuje nespravované výčty, které používá rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="ec60e-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec60e-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ec60e-104">In This Section</span></span>  
 [<span data-ttu-id="ec60e-105">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="ec60e-106">Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec60e-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="ec60e-107">CLRDataEnumMemoryFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="ec60e-108">Označuje volání, které oblasti paměti [iclrdataenummemoryregions::enummemoryregions –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) metoda by měla obsahovat.</span><span class="sxs-lookup"><span data-stu-id="ec60e-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="ec60e-109">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="ec60e-110">Určuje typ procesu vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="ec60e-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="ec60e-111">CorDebugBlockingReason – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="ec60e-112">Určuje důvody, proč může zablokování vlákna na daný objekt.</span><span class="sxs-lookup"><span data-stu-id="ec60e-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="ec60e-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="ec60e-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="ec60e-114">Označuje důvod nebo důvodů, proč inicializační řetězec volání.</span><span class="sxs-lookup"><span data-stu-id="ec60e-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="ec60e-115">CorDebugCodeInvokeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="ec60e-116">Popisuje, jak exportované funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ec60e-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="ec60e-117">CorDebugCodeInvokePurpose – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="ec60e-118">Popisuje, proč exportované funkce volá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="ec60e-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="ec60e-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="ec60e-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="ec60e-120">Poskytuje další možnosti ladění, které lze použít ve volání [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec60e-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="ec60e-121">CorDebugDebugEventKind – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="ec60e-122">Určuje typ události, jejichž informace je dekódováno pomocí [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec60e-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="ec60e-123">CorDebugDecodeEventFlagsWindows – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="ec60e-124">Poskytuje další informace o ladění událostí na platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ec60e-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="ec60e-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="ec60e-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="ec60e-126">Určuje typ zpětné volání, které se provádí ze [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) událostí.</span><span class="sxs-lookup"><span data-stu-id="ec60e-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="ec60e-127">CorDebugExceptionFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="ec60e-128">Poskytuje další informace o výjimce.</span><span class="sxs-lookup"><span data-stu-id="ec60e-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="ec60e-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="ec60e-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="ec60e-130">Určuje události, ke které je právě signalizována zpětného volání ve fázi unwind.</span><span class="sxs-lookup"><span data-stu-id="ec60e-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="ec60e-131">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="ec60e-132">Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="ec60e-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="ec60e-133">CorDebugGenerationTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="ec60e-134">Určuje generování oblast paměti na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="ec60e-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="ec60e-135">Cordebughandletype –</span><span class="sxs-lookup"><span data-stu-id="ec60e-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="ec60e-136">Určuje typ popisovače.</span><span class="sxs-lookup"><span data-stu-id="ec60e-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="ec60e-137">CorDebugIlToNativeMappingTypes – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="ec60e-138">Označuje, zda určitý rozsah nativní pokyny odpovídá speciální kód oblasti.</span><span class="sxs-lookup"><span data-stu-id="ec60e-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="ec60e-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="ec60e-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="ec60e-140">Určuje typy kódu, který může být vkročili.</span><span class="sxs-lookup"><span data-stu-id="ec60e-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="ec60e-141">CorDebugInterfaceVersion – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="ec60e-142">Určuje verzi rozhraní .NET Framework nebo verzi rozhraní .NET Framework, ve kterém byl zaveden rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ec60e-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="ec60e-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="ec60e-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="ec60e-144">Určuje typ rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ec60e-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="ec60e-145">CorDebugJITCompilerFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="ec60e-146">Obsahuje hodnoty, které ovlivňují chování spravované kompilátor just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="ec60e-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="ec60e-147">CorDebugJITCompilerFlagsDeprecated – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="ec60e-148">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="ec60e-148">Obsolete.</span></span> <span data-ttu-id="ec60e-149">Použití `CORDEBUG_JIT_DEFAULT` člena [cordebugjitcompilerflags –](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) výčet místo.</span><span class="sxs-lookup"><span data-stu-id="ec60e-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="ec60e-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="ec60e-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="ec60e-151">Poskytuje podrobnosti o způsobu získání hodnoty ukazatel instrukce (IP).</span><span class="sxs-lookup"><span data-stu-id="ec60e-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="ec60e-152">CorDebugMDAFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="ec60e-153">Určuje stav vláken, ve kterém se spustí Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="ec60e-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="ec60e-154">CorDebugNGenPolicy – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="ec60e-155">Poskytuje hodnotu, která určuje, zda ladicí program načítá nativní bitové kopie (NGen) z mezipaměti nativních bitových kopií.</span><span class="sxs-lookup"><span data-stu-id="ec60e-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="ec60e-156">CorDebugPlatform – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="ec60e-157">Poskytuje cílové platformy hodnoty, které jsou používány [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec60e-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="ec60e-158">CorDebugRecordFormat – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="ec60e-159">Popisuje formát dat v bajtové pole, která obsahuje informace o události ladění nativní výjimka.</span><span class="sxs-lookup"><span data-stu-id="ec60e-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="ec60e-160">Cordebugregister –</span><span class="sxs-lookup"><span data-stu-id="ec60e-160">CorDebugRegister</span></span>  
 <span data-ttu-id="ec60e-161">Určuje registrů spojené s danou procesor architektury.</span><span class="sxs-lookup"><span data-stu-id="ec60e-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="ec60e-162">CorDebugSetContextFlag – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="ec60e-163">Určuje, zda je kontext z aktivního (nebo listu) rámce v zásobníku nebo byl vypočítán pomocí návrat zpět z jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="ec60e-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="ec60e-164">CorDebugStateChange – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="ec60e-165">Popisuje množství dat uložených v mezipaměti, který musí být odstraněn podle změn do procesu.</span><span class="sxs-lookup"><span data-stu-id="ec60e-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="ec60e-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="ec60e-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="ec60e-167">Určuje výsledek jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="ec60e-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="ec60e-168">Cordebugthreadstate –</span><span class="sxs-lookup"><span data-stu-id="ec60e-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="ec60e-169">Určuje stav vlákna pro ladění.</span><span class="sxs-lookup"><span data-stu-id="ec60e-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="ec60e-170">\>Cordebugunmappedstop –</span><span class="sxs-lookup"><span data-stu-id="ec60e-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="ec60e-171">Určuje typ nenamapované kód, který můžete aktivovat zastavení provádění kódu pomocí krokovače.</span><span class="sxs-lookup"><span data-stu-id="ec60e-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="ec60e-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="ec60e-172">CorDebugUserState</span></span>  
 <span data-ttu-id="ec60e-173">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="ec60e-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="ec60e-174">CorGCReferenceType – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="ec60e-175">Identifikuje zdrojový objekt bude uvolněna.</span><span class="sxs-lookup"><span data-stu-id="ec60e-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="ec60e-176">ILCodeKind – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="ec60e-177">Obsahuje hodnoty, které určují, jestli je přístup k lokálním proměnným nebo kód přidaný v profileru instrumentace ReJIT ladicí program.</span><span class="sxs-lookup"><span data-stu-id="ec60e-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="ec60e-178">LoggingLevelEnum – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="ec60e-179">Určuje úroveň závažnosti popisnou zprávou, která jsou zapsána do protokolu událostí při spravovaným vláknem se zaprotokoluje událost.</span><span class="sxs-lookup"><span data-stu-id="ec60e-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="ec60e-180">LogSwitchCallReason – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="ec60e-181">Určuje operaci, která byla provedena na přepínači ladění a trasování.</span><span class="sxs-lookup"><span data-stu-id="ec60e-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="ec60e-182">VariableLocationType – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="ec60e-183">Určuje umístění nativní typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="ec60e-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="ec60e-184">WriteableMetadataUpdateMode – výčet</span><span class="sxs-lookup"><span data-stu-id="ec60e-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="ec60e-185">Obsahuje hodnoty, které určují, jestli jsou viditelné pro ladicí program v paměti aktualizace metadat.</span><span class="sxs-lookup"><span data-stu-id="ec60e-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="ec60e-186">[Výčet ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) obsahuje hodnoty, které jsou používány CLRDATA_IL_ADDRESS_MAP struktury.</span><span class="sxs-lookup"><span data-stu-id="ec60e-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ec60e-187">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ec60e-187">Related Sections</span></span>  
 [<span data-ttu-id="ec60e-188">Třídy typu coclass pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec60e-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="ec60e-189">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec60e-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="ec60e-190">Globální statické funkce pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec60e-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="ec60e-191">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ec60e-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
