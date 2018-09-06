---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb3e382a93f28ea99c66268e6e402ea275961047
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798830"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT byla zavedena v rozhraní .NET Framework verze 2.0. [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Vrátí tuto hodnotu HRESULT ve dvou scénářích:  
  
-   Při napadení profiler nuceně obnoví vlákno zaregistrujte kontext v libovolné době tak, aby vlákno pokusí o přístup k struktur, které jsou v nekonzistentním stavu.  
  
-   Když profiler pokusí o volání informační metody, které spustí uvolnění paměti z metody zpětného volání, která zakazuje uvolňování paměti.  
  
 Tyto dva scénáře jsou popsané v následujících částech.  
  
## <a name="hijacking-profilers"></a>Profilery zneužití  
 (Tento scénář je primárně problém s profilery zneužitím, i když existují případy, ve kterém profilerů bez zneužitím vidí hodnota HRESULT.)  
  
 V tomto scénáři, zneužitím profiler nuceně obnoví register kontextu vlákna v libovolné době tak, aby vlákno můžete zadat profileru kód nebo znovu zadejte common language runtime (CLR) prostřednictvím [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody.  
  
 Řada identifikátorů, že rozhraní API profilování poskytuje bod do datové struktury v CLR. Mnoho `ICorProfilerInfo` volání pouze čtení informací z těchto datových struktur a jejich předávání zpátky. CLR však může změnit věci v těchto struktur jako spuštění a může k tomu použít zámky. Předpokládejme, že modul CLR byl již držením (nebo pokusu o získání) zámku v době profiler zachycena vlákna. Pokud vlákno znovu přejde do modulu CLR a pokusí se provést další zámky, nebo zkontrolujte struktury, které se právě upravovaného, tyto struktury může být v nekonzistentním stavu. V takových situacích může dojít snadno zablokování a konflikty narušení přístupu.  
  
 Obecně platí, pokud profiler bez zneužitím spustí kód uvnitř [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metoda a zavolá `ICorProfilerInfo` metoda s platné parametry by neměly zablokování nebo přijímat narušení přístupu. Například profileru kód, který běží v rámci [icorprofilercallback::classloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metoda může požádat o informace o třídě voláním [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Metoda. Kód se může zobrazit CORPROF_E_DATAINCOMPLETE HRESULT označující, že informace nejsou k dispozici; nebudou však zablokování nebo přijímat narušení přístupu. Tato třída volá do `ICorProfilerInfo` jsou nazývány synchronní, protože byly provedeny z `ICorProfilerCallback` metody.  
  
 Ale spravovaným vláknem, který spouští kód, který není v rámci `ICorProfilerCallback` se považuje za provádět asynchronní volání metody. V rozhraní .NET Framework verze 1 bylo obtížné zjistit, co se děje v asynchronní volání. Volání může vzájemné zablokování, chybě nebo poskytnout neplatná odpověď. Rozhraní .NET Framework verze 2.0 zavedla některé jednoduché kontroly umožňuje vyhnout se tomuto problému. V rozhraní .NET Framework 2.0, při volání nebezpečné `ICorProfilerInfo` funkce asynchronně, se nezdaří s chybou CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Byla zahájena asynchronní volání nejsou obecně bezpečné. Ale následující metody jsou bezpečné a specificky podporují byla zahájena asynchronní volání:  
  
-   [Geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [Seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [GetCurrentThreadId –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [Getthreadcontext –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [Getthreadappdomain –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [Getfunctionfromip –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [Getfunctioninfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [Getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [Getcodeinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [Getcodeinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [Getmoduleinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [Getclassidinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [Getclassidinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [Isarrayclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [Setfunctionidmapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [Dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Další informace naleznete v příspěvku [důvod, proč máme CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) v blogu rozhraní API profilování CLR.  
  
## <a name="triggering-garbage-collections"></a>Aktivace uvolňování pamětí  
 Tento scénář zahrnuje profiler, který je spuštěn uvnitř metody zpětného volání (například jeden z `ICorProfilerCallback` metody), která zakazuje uvolňování paměti. Pokud se profiler pokusí volat metodu informační (například metoda na `ICorProfilerInfo` rozhraní), která může spustit uvolňování paměti, informační metoda selže s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Následující tabulka obsahuje metody zpětného volání, které zakazuje uvolnění paměti a informační metody, které můžou aktivovat uvolnění paměti. Pokud profiler spouští v jedné z metod uvedených zpětného volání a volání metod uvedených informační, informační metody se nezdaří s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody zpětného volání, které zakazuje uvolnění paměti|Informační metody, které spustí uvolnění paměti|  
|------------------------------------------------------|------------------------------------------------------------|  
|[Threadassignedtoosthread –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [Exceptionunwindfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [Exceptionunwindfunctionleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [Exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [Exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [Exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [Runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [Runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [Runtimesuspendaborted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [Runtimethreadsuspended –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [Runtimethreadresumed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [Movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [Objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [Objectsallocatedbyclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [Handlecreated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [Handledestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [Garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [Garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[Getilfunctionbodyallocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [Setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [Forcegc –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [Getclassfromtoken –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [Getclassfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [Getfunctionfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [Getappdomaininfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [Requestprofilerdetach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [Getappdomainscontainingmodule –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
