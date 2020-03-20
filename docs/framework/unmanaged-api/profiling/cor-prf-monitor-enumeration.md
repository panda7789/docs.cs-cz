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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175197"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR – výčet
Obsahuje hodnoty, které se používají k určení chování, schopnosti nebo události, ke kterým profiler chce přihlásit.  
  
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
 V následujících `COR_PRF_MONITOR` částech jsou uvedeny členy výčtu podle kategorie. Kategorie jsou:  
  
- [Nejsou nastaveny žádné příznaky.](#None)  
  
- [Příznaky zpětného volání](#Callback)  
  
- [Příznaky umožňující funkce](#Feature)  
  
- [Příznaky konfigurace](#Config)  
  
- [Složené příznaky](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Nejsou nastaveny žádné příznaky.  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nejsou nastaveny žádné příznaky.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Příznaky zpětného volání  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Řídí `AppDomainCreation*` a `AppDomainShutdown*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Řídí `AssemblyLoad*` a `AssemblyUnload*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Řídí `JITCachedFunctionSearch*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)<br /><br /> Chování tohoto příznaku se změní v rozhraní .NET Framework verze 2.0.|  
|`COR_PRF_MONITOR_CCW`|Řídí `COMClassicVTable*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Řídí `ClassLoad*` a `ClassUnload*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Řídí `ExceptionCLRCatcher*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Řídí zpětná volání [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) a [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Řídí `FunctionEnter*`globální `FunctionLeave*`statické `FunctionTailCall*`funkce a [profilování globálních statických funkcí](profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Řídí [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) zpětné volání `ExceptionSearch*` `ExceptionOSHandler*`a `ExceptionUnwind*`, `ExceptionCatcher*` , a zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Řídí zpětné volání [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_GC`|Řídí [garbagecollectionstarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), `ICorProfilerCallback*` [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)a [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) zpětná volání v rozhraních. Při `COR_PRF_MONITOR_GC` přidělení je souběžné uvolňování paměti vypnuto.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Řídí `JITCompilation*`volání [, JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)a [JITInlining](icorprofilercallback-jitinlining-method.md) v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Řídí `ModuleLoad*`volání `ModuleUnload*`, , a [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Řídí [objectallocated](icorprofilercallback-objectallocated-method.md) zpětné volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_REMOTING`|Řídí `Remoting*` zpětná volání v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Určuje, `Remoting*` zda budou zpětná volání monitorovat asynchronní události.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Určuje, zda je soubor `Remoting*` cookie předán zpětná volání.|  
|`COR_PRF_MONITOR_SUSPENDS`|Řídí `RuntimeSuspend*`zpětná `RuntimeResume*`volání , , [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)a [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) v rozhraní [ICorProfilerCallback.](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_THREADS`|Řídí [threadcreated](icorprofilercallback-threadcreated-method.md), [threaddestroyed](icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread](icorprofilercallback-threadassignedtoosthread-method.md)a [threadnamechanged](icorprofilercallback2-threadnamechanged-method.md) zpětná volání v [rozhraníI ICorProfilerCallback](icorprofilercallback-interface.md) a [ICorProfilerCallback2.](icorprofilercallback2-interface.md)|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Příznaky umožňující funkce  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umožňuje `ClassID` načtení přesné pro obecné funkce voláním [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) `COR_PRF_FRAME_INFO` metoda s hodnotou vrácenou [FunctionEnter2](functionenter2-function.md) zpětné volání.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Povolí trasování argumentů pomocí zpětného volání [FunctionEnter2](functionenter2-function.md) nebo [FunctionEnter3WithInfo](functionenter3withinfo-function.md) a metody [GetFunctionEnter3Info.](icorprofilerinfo3-getfunctionenter3info-method.md)|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Povolí trasování vrácených hodnot pomocí zpětného volání [FunctionLeave2](functionleave2-function.md) nebo [Metody FunctionLeave3WithInfo](functionleave3withinfo-function.md) a [GetFunctionLeave3Info.](icorprofilerinfo3-getfunctionleave3info-method.md)|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Zastaralé<br /><br /> V procesu ladění není podporována. Tento příznak nemá žádný vliv.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Zastaralé<br /><br /> Umožňuje profiler získat IL-to-nativní mapy pomocí [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md). Počínaje rozhraním .NET Framework 2.0, runtime vždy sleduje mapy IL-to-nativní; proto tento příznak je vždy považován za nastavený.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje za běhu, který profiler může chtít oznámení přidělení objektu. Tento příznak musí být nastaven během inicializace. Umožňuje profiler následně `COR_PRF_MONITOR_OBJECT_ALLOCATED` použít příznak pro příjem [ObjectAllocated](icorprofilercallback-objectallocated-method.md) zpětná volání.|  
|`COR_PRF_ENABLE_REJIT`|Umožňuje volání [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) a [RequestRevert](icorprofilerinfo4-requestrevert-method.md) metody. Profiler musí nastavit tento příznak při spuštění.  Pokud profiler určuje tento příznak, musí `COR_PRF_DISABLE_ALL_NGEN_IMAGES`také zadat .|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Umožňuje volání [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoda.|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Příznaky konfigurace  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Zabrání načtení všech nativních obrazů (včetně obrázků s profilerem).  Pokud tento příznak `COR_PRF_USE_PROFILE_IMAGES` a příznak `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jsou zadány, se používá.|  
|`COR_PRF_DISABLE_INLINING`|Zakáže všechny vkládání.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Zakáže všechny optimalizace kódu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Zakáže kontroly průhlednosti zabezpečení, které se obvykle provádějí během kompilace jit (just-in-time) a načítání tříd pro plně důvěryhodná sestavení. To může usnadnit provádění některých přístrojů.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Způsobí, že hledání nativního obrázku vyhledá obrazy s rozšířeným profilem. Pokud pro dané sestavení není nalezen žádný obrázek s rozšířeným profilem, za běhu společného jazyka se vrátí zpět na JIT pro toto sestavení. Pokud tento příznak `COR_PRF_DISABLE_ALL_NGEN_IMAGES` a příznak `COR_PRF_DISABLE_ALL_NGEN_IMAGES` jsou zadány, se používá.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Složené příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Představuje `COR_PRF_MONITOR` všechny hodnoty příznaku.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Představuje `COR_PRF_MONITOR` všechny příznaky, které lze nastavit po profiler je připojen ke spuštěné aplikaci. Část syntaxe označuje jednotlivé příznaky, které jsou v této bitové masce přítomny.|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Představuje `COR_PRF_MONITOR` všechny příznaky, které lze nastavit pouze během inicializace. Pokus o změnu některého z `HRESULT` těchto příznaků po inicializaci vrátí hodnotu, která označuje selhání.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Představuje `COR_PRF_MONITOR` všechny příznaky, které vyžadují obrázky s rozšířeným profilem.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `COR_PRF_MONITOR` se používá s [metodami ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) k definování oznámení událostí, která běžný jazyk runtime provede pro profiler.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro profilaci](profiling-enumerations.md)
- [GetEventMask – metoda](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask – metoda](icorprofilerinfo-seteventmask-method.md)
