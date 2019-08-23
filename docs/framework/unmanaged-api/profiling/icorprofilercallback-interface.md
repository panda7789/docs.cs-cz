---
title: ICorProfilerCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3119818934df765a8bbd9c05caaee04f9476069f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963524"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback – rozhraní
Poskytuje metody, které jsou používány modulem CLR (Common Language Runtime) k oznamování profileru kódu, když dojde k odběru událostí, ke kterým má Profiler odběr.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AppDomainCreationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Oznamuje profileru, že byla vytvořena doména aplikace.|  
|[AppDomainCreationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Oznamuje profileru, že se vytváří doména aplikace.|  
|[AppDomainShutdownFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Upozorní profileru, že doména aplikace byla uvolněna z procesu.|  
|[AppDomainShutdownStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Upozorní profileru, že doména aplikace je uvolněna z procesu.|  
|[AssemblyLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Upozorní profileru, že bylo dokončeno načítání sestavení.|  
|[AssemblyLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Upozorní profileru, že je načteno sestavení.|  
|[AssemblyUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Upozorní profileru, že bylo sestavení uvolněno.|  
|[AssemblyUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Upozorní profileru, že probíhá uvolňování sestavení.|  
|[ClassLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Upozorní profileru, že se dokončilo načítání třídy.|  
|[ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Upozorní profileru, že je načtena třída.|  
|[ClassUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Upozorní profileru, že se dokončila uvolňování třídy.|  
|[ClassUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Upozorní profileru, že je uvolněna třída.|  
|[COMClassicVTableCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Upozorní profileru, že se vytvořila obálka pro vyvolané za běhu (RCW) pro zadané IID a třídu.|  
|[COMClassicVTableDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Upozorní profileru, že je zničena aplikace RCW.|  
|[ExceptionCatcherEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Upozorňuje profileru, že řízení se předává příslušnému `catch` bloku.|  
|[ExceptionCatcherLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Upozorňuje profileru, že řízení se předává z příslušného `catch` bloku.|  
|[ExceptionCLRCatcherExecute – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Zastaralé v .NET Framework verze 2,0.|  
|[ExceptionCLRCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Zastaralé v .NET Framework 2,0.|  
|[ExceptionOSHandlerEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.|  
|[ExceptionOSHandlerLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.|  
|[ExceptionSearchCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Upozorní profileru, že ve fázi hledání výjimek byla nalezena obslužná rutina pro vyvolanou výjimku.|  
|[ExceptionSearchFilterEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Upozorní profileru, že je spuštěn filtr uživatele.|  
|[ExceptionSearchFilterLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Upozorní profileru, že uživatel právě dokončil provádění filtru.|  
|[ExceptionSearchFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Upozorní profileru, že byla zadána funkce vyhledávací fáze zpracování výjimek.|  
|[ExceptionSearchFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Upozorní profileru, že prohledávání fáze zpracování výjimek dokončila hledání funkce.|  
|[ExceptionThrown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Upozorní profileru, že byla vyvolána výjimka.|  
|[ExceptionUnwindFinallyEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Upozorní profileru, že unwind fáze zpracování výjimek zadává `finally` klauzuli obsaženou v zadané funkci.|  
|[ExceptionUnwindFinallyLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek opustila `finally` klauzuli.|  
|[ExceptionUnwindFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek zavolala funkci.|  
|[ExceptionUnwindFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek dokončila odvinutí funkce.|  
|[FunctionUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Upozorní profileru, že modul runtime zahájil uvolnění funkce.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Volá se, aby se inicializoval Profiler při každém spuštění nové aplikace CLR.|  
|[JITCachedFunctionSearchFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Upozorní profileru, že vyhledávání skončilo pro funkci, která byla zkompilována dříve pomocí nástroje NGen. exe.|  
|[JITCachedFunctionSearchStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Upozorní profileru, že bylo spuštěno vyhledávání pro funkci, která byla dříve kompilována pomocí nástroje NGen. exe.|  
|[JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Upozorní profileru, že kompilátor JIT dokončil kompilaci funkce.|  
|[JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Upozorní profileru, že kompilátor JIT (just-in-time) začal kompilovat funkci.|  
|[JITFunctionPitched – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Upozorní profileru, že byla z paměti odebrána funkce, která byla kompilována JIT.|  
|[JITInlining – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Upozorní profileru, že se chystá kompilátor JIT Vložit funkci do řádku s jinou funkcí.|  
|[ManagedToUnmanagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Upozorní profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.|  
|[ModuleAttachedToAssembly – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Upozorní profileru, že je modul připojen ke svému nadřazenému sestavení.|  
|[ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Upozorní profileru, že se dokončilo načítání modulu.|  
|[ModuleLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Upozorní profileru, že je modul načítán.|  
|[ModuleUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Upozorní profileru, že se dokončilo uvolňování modulu.|  
|[ModuleUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Upozorní profileru, že je modul uvolňován.|  
|[MovedReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Upozorní profiler na odkazy na objekty, které se přesunuly během uvolňování paměti.|  
|[ObjectAllocated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Upozorní profileru, že paměť v haldě byla přidělena pro objekt.|  
|[ObjectReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Upozorňuje Profiler na objekty v paměti, na které se odkazuje zadaný objekt.|  
|[ObjectsAllocatedByClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Upozorňuje Profiler o počtu instancí každé zadané třídy, které byly vytvořeny od předchozí kolekce uvolnění paměti.|  
|[RemotingClientInvocationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Upozorní profileru, že volání vzdálené komunikace bylo dokončeno na straně klienta.|  
|[RemotingClientInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Upozorní profileru, že bylo zahájeno volání vzdálené komunikace.|  
|[RemotingClientReceivingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Upozorní profileru, že je dokončena serverová část volání vzdálené komunikace a klient nyní přijímá a chystá zpracovat odpověď.|  
|[RemotingClientSendingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Upozorní profileru, že klient posílá požadavek na server.|  
|[RemotingServerInvocationReturned – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Upozorní profileru, že proces skončil voláním metody v reakci na požadavek na vyvolání vzdálené metody.|  
|[RemotingServerInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Upozorní profileru, že proces vyvolává volání metody v reakci na požadavek na vyvolání vzdálené metody.|  
|[RemotingServerReceivingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Upozorní profileru, že proces přijímá volání vzdálené metody nebo žádost o aktivaci.|  
|[RemotingServerSendingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Upozorní profileru, že proces dokončil zpracování žádosti o vyvolání vzdálené metody a chystá se odeslat odpověď prostřednictvím kanálu.|  
|[RootReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Oznamuje profileru informace o kořenových odkazech po uvolnění paměti.|  
|[RuntimeResumeFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Upozorní profileru, že modul runtime obnovil všechna běhová vlákna a vrátil se do normálního provozu.|  
|[RuntimeResumeStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Upozorní profileru, že modul runtime obnovuje všechna běhová vlákna.|  
|[RuntimeSuspendAborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Upozorní profileru, že modul runtime přerušil přerušení běhu, ke kterému došlo.|  
|[RuntimeSuspendFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Upozorní profileru, že modul runtime dokončil pozastavení všech vláken za běhu.|  
|[RuntimeSuspendStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Upozorní profileru, že modul runtime se chystá pozastavit všechna vlákna za běhu.|  
|[RuntimeThreadResumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Upozorní profileru, že zadané vlákno bylo po pozastavení obnoveno.|  
|[RuntimeThreadSuspended – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Upozorní profileru, že zadané vlákno bylo nebo bude pozastaveno.|  
|[Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Oznamuje profileru, že se aplikace vypíná.|  
|[ThreadAssignedToOSThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Upozorní profileru, že spravované vlákno je implementováno pomocí konkrétního vlákna operačního systému (OS).|  
|[ThreadCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Upozorní profileru, že bylo vytvořeno vlákno.|  
|[ThreadDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Upozorní profileru, že došlo ke zničení vlákna.|  
|[UnmanagedToManagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Upozorní profileru, že došlo k přechodu z nespravovaného kódu do spravovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` rozhraní (nebo [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) pro oznámení profileru, když dojde k odběru události, ke které má Profiler odběr. Toto je primární rozhraní zpětného volání, přes které CLR komunikuje s profilerem kódu.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro .NET Framework verze 2,0 nebo novější musí Profiler také implementovat `ICorProfilerCallback2` metody. Každá implementace metody musí vracet hodnotu HRESULT, která má hodnotu S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 V registru systému Microsoft Windows musí Profiler kódu zaregistrovat svůj objekt modelu COM (Component Object Model), který implementuje `ICorProfilerCallback` rozhraní a. `ICorProfilerCallback2` Profiler kódu se přihlašuje k odběru událostí, ke kterým chce dostávat oznámení voláním [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)v profileru. Profiler je pak schopný přijímat oznámení z modulu runtime, když dojde k události, která se chystá, nebo k ní došlo pouze v průběhu provádění procesu modulu runtime.  
  
> [!NOTE]
> Profiler registruje jeden objekt COM. Pokud je profiler cílen na .NET Framework verze 1,0 nebo 1,1, musí tento objekt COM implementovat pouze metody `ICorProfilerCallback`. Pokud cílí na .NET Framework verze 2,0 nebo novější, musí objekt COM také implementovat metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
