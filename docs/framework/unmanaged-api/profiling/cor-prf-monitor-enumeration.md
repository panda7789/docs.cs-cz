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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb39eb768069a737f3f89c771bf02fd6bc0c3b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599049"
---
# <a name="corprfmonitor-enumeration"></a>COR_PRF_MONITOR – výčet
Obsahuje hodnoty, které se používají k určení chování, funkce nebo události, ke kterým profileru chce odběru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Následující seznam oddílů `COR_PRF_MONITOR` členy výčtu podle kategorie. Kategorie jsou:  
  
- [Není nastaven žádný příznaky](#None)  
  
- [Příznaky zpětného volání](#Callback)  
  
- [Povolení funkce příznaky](#Feature)  
  
- [Konfigurace příznaky](#Config)  
  
- [Složený příznaky](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Není nastaven žádný příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Jsou nastaveny žádné příznaky.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Příznaky zpětného volání  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Ovládací prvky `AppDomainCreation*` a `AppDomainShutdown*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Ovládací prvky `AssemblyLoad*` a `AssemblyUnload*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Ovládací prvky `JITCachedFunctionSearch*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.<br /><br /> Chování tohoto příznaku se změnilo v rozhraní .NET Framework verze 2.0.|  
|`COR_PRF_MONITOR_CCW`|Ovládací prvky `COMClassicVTable*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Ovládací prvky `ClassLoad*` a `ClassUnload*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Ovládací prvky `ExceptionCLRCatcher*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Ovládací prvky [unmanagedtomanagedtransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) a [managedtounmanagedtransition –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Ovládací prvky `FunctionEnter*`, `FunctionLeave*`, a `FunctionTailCall*` [profilace globálních statických funkcí](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Ovládací prvky [exceptionthrown –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) zpětného volání a `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, a `ExceptionCatcher*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Ovládací prvky [functionunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) zpětného volání v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_GC`|Ovládací prvky [garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [ Survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [survivingreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [objectsallocatedbyclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [ Rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [handlecreated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [handledestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), a [finalizeableobjectqueued – ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) zpětnými voláními v `ICorProfilerCallback*` rozhraní.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Ovládací prvky `JITCompilation*`, [jitfunctionpitched –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), a [jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Ovládací prvky `ModuleLoad*`, `ModuleUnload*`, a [moduleattachedtoassembly –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Ovládací prvky [objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) zpětného volání v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_REMOTING`|Ovládací prvky `Remoting*` zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Ovládací prvky, zda `Remoting*` zpětná volání budou sledovány události asynchronní.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Určuje, zda je předán do souboru cookie `Remoting*` zpětná volání.|  
|`COR_PRF_MONITOR_SUSPENDS`|Ovládací prvky `RuntimeSuspend*`, `RuntimeResume*`, [runtimethreadsuspended –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), a [runtimethreadresumed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní.|  
|`COR_PRF_MONITOR_THREADS`|Ovládací prvky [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [threaddestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [threadassignedtoosthread –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), a [threadnamechanged –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) zpětnými voláními v [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) rozhraní.|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Povolení funkce příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Umožňuje načítání přesná `ClassID` pro obecnou funkci voláním [getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody `COR_PRF_FRAME_INFO` hodnoty vrácené [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Pomocí trasování umožňuje argument [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání nebo [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) zpětného volání a [getfunctionenter3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) metoda.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Zapíná trasování vrácených hodnot s použitím [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání nebo [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) zpětného volání a [getfunctionleave3info –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) metody.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Zastaralé<br /><br /> V procesu ladění není podporováno. Tento příznak nemá žádný vliv.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Zastaralé<br /><br /> Umožňuje získat IL na nativní mapy pomocí profileru [getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). Od verze rozhraní .NET Framework 2.0, modul runtime vždy sleduje IL na nativní mapy; proto tento příznak je vždy považován za nastavit.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informuje o modulu runtime, že profiler může být vhodné oznámení přidělení objektu. Tento příznak musí být nastavena během inicializace. To umožňuje profileru následně použít `COR_PRF_MONITOR_OBJECT_ALLOCATED` příznak pro příjem [objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) zpětná volání.|  
|`COR_PRF_ENABLE_REJIT`|Umožňuje volání [requestrejit –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) a [requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody. Profiler musí tento příznak nastavit na spuštění.  Pokud profiler určuje tento příznak, kromě toho musí určovat `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Umožňuje volání [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Konfigurace příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Brání všechny nativní bitové kopie (včetně profilerem vylepšené imagí) načtení.  Pokud tento příznak a `COR_PRF_USE_PROFILE_IMAGES` je zadán příznak, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` se používá.|  
|`COR_PRF_DISABLE_INLINING`|Zakáže všechny vkládání.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Zakáže všechny optimalizace kódu.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Zakáže transparentnosti kontroly zabezpečení, které jsou obvykle provádí během just-in-time (JIT) kompilaci a třídu načítající pro plně důvěryhodná sestavení. Některé instrumentace může být jednodušší provádět.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Způsobí, že hledání nativní bitové kopie k vyhledání profilerem vylepšené imagí. Pokud pro dané sestavení nebyl nalezen žádný profilerem vylepšené obrázek, modul common language runtime přejde do prostředí JIT pro toto sestavení. Pokud tento příznak a `COR_PRF_DISABLE_ALL_NGEN_IMAGES` je zadán příznak, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` se používá.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Složený příznaky  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_ALL`|Představuje všechny `COR_PRF_MONITOR` příznak hodnoty.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Představuje všechny `COR_PRF_MONITOR` příznaky, které je možné nastavit poté, co je profiler připojen ke spuštěné aplikaci. V části Syntaxe určuje příznaky, které se nacházejí v této bitové masky.|  
|`COR_PRF_MONITOR_ALL`|Povolí všechny události zpětného volání.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Představuje všechny `COR_PRF_MONITOR` příznaky, které lze nastavit pouze během inicializace. Změnit některý z těchto příznaků po inicializaci vrátí `HRESULT` hodnotu, která indikuje selhání.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Představuje všechny `COR_PRF_MONITOR` příznaky, které vyžadují profil vylepšené bitové kopie.|  
  
## <a name="remarks"></a>Poznámky  
 A `COR_PRF_MONITOR` hodnota se používá s [icorprofilerinfo::geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody k definování oznamování událostí, které provádí modul common language runtime profiler.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
