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
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500803"
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
 V následujících oddílech jsou uvedeny `COR_PRF_MONITOR` členy výčtu podle kategorie. Kategorie jsou:  
  
- [Nejsou nastavené žádné příznaky.](#None)  
  
- [Příznaky zpětného volání](#Callback)  
  
- [Funkce – aktivace příznaků](#Feature)  
  
- [Příznaky konfigurace](#Config)  
  
- [Složené příznaky](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Nejsou nastavené žádné příznaky.  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nejsou nastavené žádné příznaky.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Příznaky zpětného volání  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Ovládá `AppDomainCreation*` `AppDomainShutdown*` zpětná volání a v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Ovládá `AssemblyLoad*` `AssemblyUnload*` zpětná volání a v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Řídí `JITCachedFunctionSearch*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .<br /><br /> Chování tohoto příznaku se změní v .NET Framework verze 2,0.|  
|`COR_PRF_MONITOR_CCW`|Řídí `COMClassicVTable*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Ovládá `ClassLoad*` `ClassUnload*` zpětná volání a v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Řídí `ExceptionCLRCatcher*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Řídí zpětná volání [UnmanagedToManagedTransition –](icorprofilercallback-unmanagedtomanagedtransition-method.md) a [ManagedToUnmanagedTransition –](icorprofilercallback-managedtounmanagedtransition-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Ovládá `FunctionEnter*` `FunctionLeave*` `FunctionTailCall*` [globální statické funkce, a profilování](profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Řídí zpětné volání [exceptionthrown –](icorprofilercallback-exceptionthrown-method.md) a `ExceptionSearch*` `ExceptionOSHandler*` `ExceptionUnwind*` zpětná volání,, a `ExceptionCatcher*` v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Řídí zpětné volání [functionunloadstarted –](icorprofilercallback-functionunloadstarted-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_GC`|Řídí [GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences –](icorprofilercallback-movedreferences-method.md), [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2 –](icorprofilercallback4-survivingreferences2-method.md), [objectReferences –](icorprofilercallback-objectreferences-method.md), [objectsallocatedbyclass –](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences –](icorprofilercallback-rootreferences-method.md), [RootReferences2 –](icorprofilercallback2-rootreferences2-method.md), [HandleCreated –](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed –](icorprofilercallback2-handledestroyed-method.md)a [FinalizeableObjectQueued –](icorprofilercallback2-finalizeableobjectqueued-method.md) zpětná volání v `ICorProfilerCallback*` rozhraních. Při `COR_PRF_MONITOR_GC` přidělení je souběžné uvolňování paměti vypnuto.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Řídí `JITCompilation*` zpětná volání, [Jitfunctionpitched –](icorprofilercallback-jitfunctionpitched-method.md)a [JITInlining –](icorprofilercallback-jitinlining-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Ovládá `ModuleLoad*` `ModuleUnload*` zpětná volání [ModuleAttachedToAssembly –](icorprofilercallback-moduleattachedtoassembly-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Řídí zpětné volání [ObjectAllocated –](icorprofilercallback-objectallocated-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING`|Řídí `Remoting*` zpětná volání v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Určuje, zda `Remoting*` zpětná volání budou monitorovat asynchronní události.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Určuje, zda je soubor cookie předán `Remoting*` zpětná volání.|  
|`COR_PRF_MONITOR_SUSPENDS`|Řídí `RuntimeSuspend*` `RuntimeResume*` zpětná volání, [runtimethreadsuspended –](icorprofilercallback-runtimethreadsuspended-method.md)a [runtimethreadresumed –](icorprofilercallback-runtimethreadresumed-method.md) v rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_THREADS`|Řídí zpětná volání [ThreadCreated –](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed –](icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread –](icorprofilercallback-threadassignedtoosthread-method.md)a [threadnamechanged –](icorprofilercallback2-threadnamechanged-method.md) v rozhraních [ICorProfilerCallback](icorprofilercallback-interface.md) a [ICorProfilerCallback2](icorprofilercallback2-interface.md) .|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Funkce – aktivace příznaků  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umožňuje načtení přesného `ClassID` pro obecnou funkci voláním metody [GetFunctionInfo2 –](icorprofilerinfo2-getfunctioninfo2-method.md) s `COR_PRF_FRAME_INFO` hodnotou vrácenou zpětným voláním [FunctionEnter2](functionenter2-function.md) .|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Povolí trasování argumentů pomocí zpětného volání [FunctionEnter2](functionenter2-function.md) nebo zpětného volání [Functionenter3withinfo –](functionenter3withinfo-function.md) a metody [GetFunctionEnter3Info –](icorprofilerinfo3-getfunctionenter3info-method.md) .|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Umožňuje trasování vrácených hodnot pomocí zpětného volání [FunctionLeave2 –](functionleave2-function.md) nebo metody zpětného volání [FunctionLeave3WithInfo –](functionleave3withinfo-function.md) a [GetFunctionLeave3Info –](icorprofilerinfo3-getfunctionleave3info-method.md) .|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Zastaralé<br /><br /> V procesu ladění není podporováno. Tento příznak nemá žádný vliv.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Zastaralé<br /><br /> Umožňuje profileru získat pomocí [GetILToNativeMapping –](icorprofilerinfo-getiltonativemapping-method.md)mapy Il-to-Native. Počínaje .NET Framework 2,0, modul runtime vždycky sleduje mapy IL-to-Native; Proto je tento příznak vždy považován za nastavený.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje modul runtime o tom, že Profiler může chtít oznámení o přidělení objektů. Tento příznak musí být nastaven během inicializace. Umožňuje profileru později použít `COR_PRF_MONITOR_OBJECT_ALLOCATED` příznak pro příjem zpětných volání [ObjectAllocated –](icorprofilercallback-objectallocated-method.md) .|  
|`COR_PRF_ENABLE_REJIT`|Povoluje volání metod [RequestReJIT –](icorprofilerinfo4-requestrejit-method.md) a [RequestRevert –](icorprofilerinfo4-requestrevert-method.md) . Profiler musí při spuštění tento příznak nastavit.  Pokud profiler tento příznak určuje, musí také zadat `COR_PRF_DISABLE_ALL_NGEN_IMAGES` .|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Povoluje volání metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Příznaky konfigurace  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zabraňuje načtení všech nativních imagí (včetně imagí s rozšířeným profilerem).  Pokud tento příznak a `COR_PRF_USE_PROFILE_IMAGES` příznak jsou zadány současně, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` je použit.|  
|`COR_PRF_DISABLE_INLINING`|Zakáže veškeré vkládání.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Zakáže všechny optimalizace kódu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Zakáže kontroly transparentnosti zabezpečení, které se obvykle provádějí během kompilace JIT (just-in-time) a načítání tříd pro sestavení s úplným vztahem důvěryhodnosti. Díky tomu je možné usnadnit provádění některých instrumentace.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Způsobí, že vyhledávání nativních imagí vyhledá obrázky vylepšené v profileru. Pokud se pro dané sestavení nenajde žádná image s rozšířeným profilerem, modul CLR (Common Language Runtime) přejde zpět na JIT pro toto sestavení. Pokud tento příznak a `COR_PRF_DISABLE_ALL_NGEN_IMAGES` příznak jsou zadány současně, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` je použit.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Složené příznaky  
  
|Člen|Description|  
|------------|-----------------|  
|`COR_PRF_ALL`|Představuje všechny `COR_PRF_MONITOR` hodnoty příznaků.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Představuje všechny `COR_PRF_MONITOR` příznaky, které lze nastavit po připojení profileru ke spuštěné aplikaci. Oddíl syntax označuje jednotlivé příznaky, které jsou k dispozici v této maskování.|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Představuje všechny `COR_PRF_MONITOR` příznaky, které lze nastavit pouze během inicializace. Pokus o změnu některého z těchto příznaků po inicializaci vrátí `HRESULT` hodnotu, která označuje selhání.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Představuje všechny `COR_PRF_MONITOR` příznaky, které vyžadují image s rozšířeným profilem.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_MONITOR`Hodnota se používá s metodami [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) k definování oznámení události, které modul CLR (Common Language Runtime) provede profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
- [GetEventMask – metoda](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask – metoda](icorprofilerinfo-seteventmask-method.md)
