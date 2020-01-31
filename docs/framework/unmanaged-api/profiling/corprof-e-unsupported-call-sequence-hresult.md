---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: b4ab5c8f7cdca1303cb4fbbc4fa39db3c5977c15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867006"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT byla představena v .NET Framework verze 2,0. .NET Framework 4 vrátí tuto hodnotu HRESULT ve dvou scénářích:  
  
- V případě, že napadený Profiler vynuceně obnoví kontext registru vlákna v čase, takže se vlákno pokusí získat přístup ke strukturám, které jsou v nekonzistentním stavu.  
  
- Když se Profiler pokusí zavolat informační metodu, která spustí uvolňování paměti z metody zpětného volání, která zakazuje uvolňování paměti.  
  
Tyto dva scénáře jsou popsány v následujících částech.  
  
## <a name="hijacking-profilers"></a>Napadení profilerů  

  (Tento scénář je primárně problémem při napadení profilerů, i když existují případy, kdy se tato hodnota HRESULT může zobrazit v profilech nenapadení.)  
  
 V tomto scénáři Profiler vynuceně resetuje kontext registru vlákna v libovolném čase tak, aby vlákno mohlo zadat kód profileru nebo znovu zadat modul CLR (Common Language Runtime) prostřednictvím metody [ICorProfilerInfo](icorprofilerinfo-interface.md) .  
  
 Mnohé z identifikátorů, které rozhraní API profilování poskytuje, odkazuje na datové struktury v modulu CLR. Mnoho `ICorProfilerInfo` volá pouze čtení informací z těchto datových struktur a převrací je zpět. Modul CLR se však může v těchto strukturách měnit, když je spuštěn, a může k tomu použít zámky. Předpokládejme, že CLR již drží (nebo se pokoušel získat) zámek v době, kdy Profiler napaden vlákno. Pokud vlákno znovu zadá modul CLR a pokusí se získat více zámků nebo kontrolovat struktury, které byly právě upravovány, mohou být tyto struktury v nekonzistentním stavu. V takových situacích se můžou v takových situacích snadno zablokovat a může dojít k narušení přístupu.  
  
 Obecně platí, že když Profiler bez zneužití spustí kód uvnitř metody [ICorProfilerCallback](icorprofilercallback-interface.md) a zavolá do metody `ICorProfilerInfo` s platnými parametry, neměl by se zablokovat nebo získat porušení přístupu. Například kód profileru, který běží uvnitř metody [ICorProfilerCallback:: ClassLoadFinished –](icorprofilercallback-classloadfinished-method.md) , může požádat o informace o třídě voláním metody [ICorProfilerInfo2:: GetClassIDInfo2 –](icorprofilerinfo2-getclassidinfo2-method.md) . Kód může obdržet CORPROF_E_DATAINCOMPLETE HRESULT, aby označoval, že informace nejsou k dispozici. Nicméně nebude zablokovat ani přijímat porušení přístupu. Tato volání do `ICorProfilerInfo` jsou považována za synchronní, protože jsou vytvořena z metody `ICorProfilerCallback`.  
  
 Nicméně spravované vlákno, které spouští kód, který není v rámci `ICorProfilerCallback` metoda, je považováno za asynchronní volání. Ve .NET Framework verze 1 bylo obtížné určit, co se může stát v asynchronním volání. Volání může zablokovat, selhat nebo poskytnout neplatnou odpověď. .NET Framework verze 2,0 představila některé jednoduché kontroly, které vám pomůžou se vyhnout tomuto problému. Pokud je v .NET Framework 2,0 volána nebezpečná `ICorProfilerInfo` funkce asynchronně, dojde k chybě s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Obecně nejsou asynchronní volání bezpečná. Následující metody jsou však bezpečné a konkrétně podporují asynchronní volání:  
  
- [GetEventMask](icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext –](icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Další informace najdete v tématu [proč CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) na blogu rozhraní API pro profilaci CLR.  
  
## <a name="triggering-garbage-collections"></a>Aktivují se uvolňování paměti.  
 Tento scénář zahrnuje Profiler, který běží uvnitř metody zpětného volání (například jedna z metod `ICorProfilerCallback`), která zakazuje uvolňování paměti. Pokud se Profiler pokusí zavolat informační metodu (například metodu v rozhraní `ICorProfilerInfo`), která může spustit uvolňování paměti, informační metoda se nezdařila s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 V následující tabulce jsou uvedeny metody zpětného volání, které zakazují uvolňování paměti, a informativní metody, které mohou aktivovat uvolňování paměti. Pokud se profiler provádí uvnitř jedné z uvedených metod zpětného volání a volá jednu z uvedených informativních metod, tato informační metoda se nezdařila s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody zpětného volání, které zakazují uvolňování paměti|Informační metody, které spouštějí uvolňování paměti|  
|------------------------------------------------------|------------------------------------------------------------|  
|[Threadassignedtoosthread –](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [Runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [Runtimesuspendaborted –](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [Runtimethreadsuspended –](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [Runtimethreadresumed –](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences –](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences –](icorprofilercallback-objectreferences-method.md)<br /><br /> [Objectsallocatedbyclass –](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 –](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed –](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 – rozhraní](icorprofilercallback3-interface.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
