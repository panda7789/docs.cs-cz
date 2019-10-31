---
title: COR_PRF_MONITOR – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 321ad53ca5f773191c5b5d1084b36caa6aeae4dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137049"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR – výčet
Obsahuje hodnoty, které slouží k určení chování, schopností nebo událostí, ke kterým se chce Profiler přihlásit k odběru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Členové  
 Následující části uvádějí `COR_PRF_MONITOR` členů výčtu podle kategorie. Kategorie jsou:  
  
- [Nejsou nastavené žádné příznaky.](#None)  
  
- [Příznaky zpětného volání](#Callback)  
  
- [Funkce – aktivace příznaků](#Feature)  
  
- [Příznaky konfigurace](#Config)  
  
- [Složené příznaky](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Nejsou nastavené žádné příznaky.  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nejsou nastavené žádné příznaky.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Příznaky zpětného volání  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Řídí `AppDomainCreation*` a `AppDomainShutdown*` zpětná volání v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Řídí `AssemblyLoad*` a `AssemblyUnload*` zpětná volání v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Řídí zpětná volání `JITCachedFunctionSearch*` v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .<br /><br /> Chování tohoto příznaku se změní v .NET Framework verze 2,0.|  
|`COR_PRF_MONITOR_CCW`|Řídí zpětná volání `COMClassicVTable*` v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Řídí `ClassLoad*` a `ClassUnload*` zpětná volání v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Řídí zpětná volání `ExceptionCLRCatcher*` v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Řídí zpětná volání [UnmanagedToManagedTransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) a [ManagedToUnmanagedTransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Řídí [globální statické funkce profilace](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)`FunctionEnter*`, `FunctionLeave*`a `FunctionTailCall*`.|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Řídí zpětné volání [exceptionthrown –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) a `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`a `ExceptionCatcher*` zpětných volání v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Řídí zpětné volání [functionunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_GC`|Řídí [GarbageCollectionStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [ Objectsallocatedbyclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [HandleDestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)a zpětná volání [FinalizeableObjectQueued –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) v rozhraních `ICorProfilerCallback*`. Při přidělení `COR_PRF_MONITOR_GC` je souběžné uvolňování paměti vypnuto.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Řídí zpětná volání `JITCompilation*`, [jitfunctionpitched –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)a [JITInlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Řídí `ModuleLoad*`, `ModuleUnload*`a zpětná volání [ModuleAttachedToAssembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Řídí zpětné volání [ObjectAllocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING`|Řídí zpětná volání `Remoting*` v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Určuje, zda `Remoting*` zpětná volání budou monitorovat asynchronní události.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Určuje, zda je soubor cookie předán `Remoting*`ovým zpětným voláním.|  
|`COR_PRF_MONITOR_SUSPENDS`|Řídí zpětná volání `RuntimeSuspend*`, `RuntimeResume*`, [runtimethreadsuspended –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)a [Runtimethreadresumed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) v rozhraní [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_THREADS`|Řídí zpětná volání [ThreadCreated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [ThreadDestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)a [threadnamechanged –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) v rozhraních [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) .|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Funkce – aktivace příznaků  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umožňuje načtení přesného `ClassID` pro obecnou funkci voláním metody [GetFunctionInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) s hodnotou `COR_PRF_FRAME_INFO` vrácenou zpětným voláním [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) .|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Povolí trasování argumentů pomocí zpětného volání [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) nebo zpětného volání [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) a metody [GetFunctionEnter3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) .|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Umožňuje trasování vrácených hodnot pomocí zpětného volání [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) nebo metody zpětného volání [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) a [GetFunctionLeave3Info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) .|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Zastaralé<br /><br /> V procesu ladění není podporováno. Tento příznak nemá žádný vliv.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Zastaralé<br /><br /> Umožňuje profileru získat pomocí [GetILToNativeMapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)mapy Il-to-Native. Počínaje .NET Framework 2,0, modul runtime vždycky sleduje mapy IL-to-Native; Proto je tento příznak vždy považován za nastavený.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje modul runtime o tom, že Profiler může chtít oznámení o přidělení objektů. Tento příznak musí být nastaven během inicializace. Umožňuje profileru později použít příznak `COR_PRF_MONITOR_OBJECT_ALLOCATED` pro příjem zpětných volání [ObjectAllocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) .|  
|`COR_PRF_ENABLE_REJIT`|Povoluje volání metod [RequestReJIT –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) a [RequestRevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) . Profiler musí při spuštění tento příznak nastavit.  Pokud profiler tento příznak určuje, musí také zadat `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Povoluje volání metody [DoStackSnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Příznaky konfigurace  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zabraňuje načtení všech nativních imagí (včetně imagí s rozšířeným profilerem).  Je-li tento příznak a příznak `COR_PRF_USE_PROFILE_IMAGES` zadán, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` použito.|  
|`COR_PRF_DISABLE_INLINING`|Zakáže veškeré vkládání.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Zakáže všechny optimalizace kódu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Zakáže kontroly transparentnosti zabezpečení, které se obvykle provádějí během kompilace JIT (just-in-time) a načítání tříd pro sestavení s úplným vztahem důvěryhodnosti. Díky tomu je možné usnadnit provádění některých instrumentace.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Způsobí, že vyhledávání nativních imagí vyhledá obrázky vylepšené v profileru. Pokud se pro dané sestavení nenajde žádná image s rozšířeným profilerem, modul CLR (Common Language Runtime) přejde zpět na JIT pro toto sestavení. Je-li tento příznak a příznak `COR_PRF_DISABLE_ALL_NGEN_IMAGES` zadán, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` použito.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Složené příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Představuje všechny hodnoty příznaků `COR_PRF_MONITOR`.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Představuje všechny příznaky `COR_PRF_MONITOR`, které lze nastavit po připojení profileru ke spuštěné aplikaci. Oddíl syntax označuje jednotlivé příznaky, které jsou k dispozici v této maskování.|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Představuje všechny příznaky `COR_PRF_MONITOR`, které lze nastavit pouze během inicializace. Pokus o změnu některého z těchto příznaků po inicializaci vrátí `HRESULT` hodnotu, která označuje selhání.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Představuje všechny příznaky `COR_PRF_MONITOR`, které vyžadují image s rozšířeným profilem.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `COR_PRF_MONITOR` se používá s metodami [ICorProfilerInfo:: GetEventMask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) k definování oznámení události, které modul CLR (Common Language Runtime) provede v profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
