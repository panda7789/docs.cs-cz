---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: a0b117949190bcaffc334c208fff6e04a6a2c5bf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964505"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT byla představena v .NET Framework verze 2,0. .NET Framework 4 vrátí tuto hodnotu HRESULT ve dvou scénářích:  
  
- V případě, že napadený Profiler vynuceně obnoví kontext registru vlákna v čase, takže se vlákno pokusí získat přístup ke strukturám, které jsou v nekonzistentním stavu.  
  
- Když se Profiler pokusí zavolat informační metodu, která spustí uvolňování paměti z metody zpětného volání, která zakazuje uvolňování paměti.  
  
 Tyto dva scénáře jsou popsány v následujících částech.  
  
## <a name="hijacking-profilers"></a>Napadení profilerů  
 (Tento scénář je primárně problémem se napadením profilerů, i když existují případy, kdy se tato hodnota HRESULT může zobrazit v profilech nenapadení.)  
  
 V tomto scénáři Profiler vynuceně resetuje kontext registru vlákna v libovolném čase tak, aby vlákno mohlo zadat kód profileru nebo znovu zadat modul CLR (Common Language Runtime) prostřednictvím metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .  
  
 Mnohé z identifikátorů, které rozhraní API profilování poskytuje, odkazuje na datové struktury v modulu CLR. Mnoho `ICorProfilerInfo` volá pouze čtení informací z těchto datových struktur a převrací je zpět. Modul CLR se však může v těchto strukturách měnit, když je spuštěn, a může k tomu použít zámky. Předpokládejme, že CLR již drží (nebo se pokoušel získat) zámek v době, kdy Profiler napaden vlákno. Pokud vlákno znovu zadá modul CLR a pokusí se o provedení více zámků nebo kontrole struktur, které byly právě upravovány, mohou být tyto struktury v nekonzistentním stavu. V takových situacích se můžou v takových situacích snadno zablokovat a může dojít k narušení přístupu.  
  
 Obecně platí, že když Profiler bez zneužití spustí kód uvnitř metody [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a zavolá do metody `ICorProfilerInfo` s platnými parametry, neměl by se zablokovat nebo získat porušení přístupu. Například kód profileru, který běží uvnitř metody [ICorProfilerCallback:: ClassLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) , může požádat o informace o třídě voláním metody [ICorProfilerInfo2:: GetClassIDInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) . Kód může obdržet CORPROF_E_DATAINCOMPLETE HRESULT, aby označoval, že informace nejsou k dispozici; Nicméně nebude zablokovat ani přijímat porušení přístupu. Tato třída volání do `ICorProfilerInfo` se nazývá synchronní, protože je vytvořena z metody `ICorProfilerCallback`.  
  
 Nicméně spravované vlákno, které spouští kód, který není v rámci `ICorProfilerCallback` metoda, je považováno za asynchronní volání. Ve .NET Framework verze 1 bylo obtížné určit, co se může stát v asynchronním volání. Volání může zablokovat, selhat nebo poskytnout neplatnou odpověď. .NET Framework verze 2,0 představila několik jednoduchých kontrol, které vám pomůžou se vyhnout tomuto problému. Pokud je v .NET Framework 2,0 volána nebezpečná `ICorProfilerInfo` funkce asynchronně, dojde k chybě s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Obecně nejsou asynchronní volání bezpečná. Následující metody jsou však bezpečné a konkrétně podporují asynchronní volání:  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Další informace najdete v tématu [proč CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) na blogu rozhraní API pro profilaci CLR.  
  
## <a name="triggering-garbage-collections"></a>Aktivují se uvolňování paměti.  
 Tento scénář zahrnuje Profiler, který běží uvnitř metody zpětného volání (například jedna z metod `ICorProfilerCallback`), která zakazuje uvolňování paměti. Pokud se Profiler pokusí zavolat informační metodu (například metodu v rozhraní `ICorProfilerInfo`), která může spustit uvolňování paměti, informační metoda se nezdařila s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 V následující tabulce jsou uvedeny metody zpětného volání, které zakazují uvolňování paměti, a informativní metody, které mohou aktivovat uvolňování paměti. Pokud se profiler provádí uvnitř jedné z uvedených metod zpětného volání a volá jednu z uvedených informativních metod, tato informační metoda se nezdařila s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody zpětného volání, které zakazují uvolňování paměti|Informační metody, které spouštějí uvolňování paměti|  
|------------------------------------------------------|------------------------------------------------------------|  
|[Threadassignedtoosthread –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [Runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [Runtimesuspendaborted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [Runtimethreadsuspended –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [Runtimethreadresumed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [Objectsallocatedbyclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
