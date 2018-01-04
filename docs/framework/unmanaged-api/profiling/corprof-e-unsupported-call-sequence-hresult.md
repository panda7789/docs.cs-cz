---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3694e08555df3ad91fbfcc35b6eb385bd24ce3c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT byla zavedena v rozhraní .NET Framework verze 2.0. [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Vrátí tuto HRESULT ve dvou scénářích:  
  
-   Pokud zneužití profileru vynuceně resetuje podprocesu zaregistrujte kontextu v libovolnou dobu tak, aby vlákno pokusí o přístup k struktury, které jsou v nekonzistentním stavu.  
  
-   Když profileru se pokusí zavolat metodu informační, která aktivuje uvolňování paměti z metody zpětného volání, která zakazuje uvolňování paměti.  
  
 Tyto dva scénáře jsou popsané v následujících částech.  
  
## <a name="hijacking-profilers"></a>Profilery zneužití  
 (Tento scénář je primárně problém s weby profilery, i když existují případy, kdy bez zneužití profilery uvidí tento HRESULT.)  
  
 V tomto scénáři zneužití profileru vynuceně resetuje registrace podprocesu v libovolnou dobu tak, aby vlákno můžete zadat kód profileru nebo znovu zadat modul CLR (CLR) prostřednictvím [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metoda.  
  
 Mnoho ID, že profilaci API poskytuje bod datové struktury v modulu CLR. Mnoho `ICorProfilerInfo` volání jenom čtení informací z tyto datové struktury a předat je zpět. Modulu CLR však může změnit věcí v těchto struktur, jako spuštění a může k tomu použít zámky. Předpokládejme, že modulu CLR byl již podržíte (nebo při pokusu získat) zámku v době profileru napadeny vlákno. Pokud vlákno znovu zadá modulu CLR a pokusí se provést další zámky nebo zkontrolujte struktury, které byly právě upravována, tyto struktury může být v nekonzistentním stavu. V takových situacích může dojít k snadno jejich blokování a porušení přístupu.  
  
 Obecně platí, když není zneužití profileru spustí kód uvnitř [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metoda a volání `ICorProfilerInfo` metoda s platné parametry, by neměl zablokování nebo příjmu porušení přístupu. Například profileru kód, který běží v rámci [icorprofilercallback::classloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metoda může požádat o informace o třídě voláním [ICorProfilerInfo2::getclassidinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) Metoda. Kód se může zobrazit HRESULT CORPROF_E_DATAINCOMPLETE indikující, zda jsou informace k dispozici; je však nebude zablokování nebo přijímat porušení přístupu. Tato třída volání do `ICorProfilerInfo` se nazývají synchronní, protože byly provedeny z `ICorProfilerCallback` metoda.  
  
 Ale spravovaných vláken, která se spouští kód, který není v rozsahu `ICorProfilerCallback` se považuje za provádět asynchronního volání metody. V rozhraní .NET Framework verze 1 bylo obtížné určit, čemu dojde v asynchronního volání. Volání může zablokování, dojít k chybě nebo mu dávat neplatná odpověď. Rozhraní .NET Framework verze 2.0 zavedl nějaké jednoduché kontroly umožňující vyhnout se tento problém. V rozhraní .NET Framework 2.0, když zavoláte nezabezpečený `ICorProfilerInfo` fungovat asynchronně, se nezdaří s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Asynchronní volání obecně nejsou bezpečné. Ale tyto metody jsou bezpečné a konkrétně podporovat asynchronní volání:  
  
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
  
 Další informace naleznete v příspěvku [proto máme CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](http://go.microsoft.com/fwlink/?LinkId=169156) v blogu CLR profilace API.  
  
## <a name="triggering-garbage-collections"></a>Spouštěcí kolekce paměti  
 Tento scénář zahrnuje profileru, které běží uvnitř metody zpětného volání (například jeden z `ICorProfilerCallback` metody) který zakazuje uvolňování paměti. Pokud se pokusí zavolat metodu informační profileru (například metoda na `ICorProfilerInfo` rozhraní), který může aktivovat uvolnění paměti, informační metoda selže s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
 Následující tabulka zobrazuje metody zpětného volání, které nezakazuje kolekce a informační metody, které mohou aktivovat kolekce. Pokud profileru provede uvnitř jednu z uvedených zpětného volání metod a volání jednu z uvedených informační metod, že informační metoda selže s CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT.  
  
|Metody zpětného volání, které nezakazuje kolekce paměti|Informační metody, které aktivují kolekce|  
|------------------------------------------------------|------------------------------------------------------------|  
|[Threadassignedtoosthread –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [Exceptionunwindfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [Exceptionunwindfunctionleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [Exceptionunwindfinallyenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [Exceptionunwindfinallyleave –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [Exceptioncatcherenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [Runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [Runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [Runtimesuspendaborted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [Runtimethreadsuspended –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [Runtimethreadresumed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [Movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [Objectsallocatedbyclass –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [Rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [Handlecreated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [Handledestroyed –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [Garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [Garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[Getilfunctionbodyallocator –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [Setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [Setilinstrumentedcodemap –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [Forcegc –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [Getclassfromtoken –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [Getclassfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [Getfunctionfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [Getappdomaininfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [Enummodules –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [Requestprofilerdetach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [Getappdomainscontainingmodule –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
