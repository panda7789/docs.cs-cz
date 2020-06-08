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
ms.openlocfilehash: 6a53b9b1b061c2ca07a469abc78c07ed9e710069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500088"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback – rozhraní
Poskytuje metody, které jsou používány modulem CLR (Common Language Runtime) k oznamování profileru kódu, když dojde k odběru událostí, ke kterým má Profiler odběr.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[AppDomainCreationFinished – metoda](icorprofilercallback-appdomaincreationfinished-method.md)|Oznamuje profileru, že byla vytvořena doména aplikace.|  
|[AppDomainCreationStarted – metoda](icorprofilercallback-appdomaincreationstarted-method.md)|Oznamuje profileru, že se vytváří doména aplikace.|  
|[AppDomainShutdownFinished – metoda](icorprofilercallback-appdomainshutdownfinished-method.md)|Upozorní profileru, že doména aplikace byla uvolněna z procesu.|  
|[AppDomainShutdownStarted – metoda](icorprofilercallback-appdomainshutdownstarted-method.md)|Upozorní profileru, že doména aplikace je uvolněna z procesu.|  
|[AssemblyLoadFinished – metoda](icorprofilercallback-assemblyloadfinished-method.md)|Upozorní profileru, že bylo dokončeno načítání sestavení.|  
|[AssemblyLoadStarted – metoda](icorprofilercallback-assemblyloadstarted-method.md)|Upozorní profileru, že je načteno sestavení.|  
|[AssemblyUnloadFinished – metoda](icorprofilercallback-assemblyunloadfinished-method.md)|Upozorní profileru, že bylo sestavení uvolněno.|  
|[AssemblyUnloadStarted – metoda](icorprofilercallback-assemblyunloadstarted-method.md)|Upozorní profileru, že probíhá uvolňování sestavení.|  
|[ClassLoadFinished – metoda](icorprofilercallback-classloadfinished-method.md)|Upozorní profileru, že se dokončilo načítání třídy.|  
|[ClassLoadStarted – metoda](icorprofilercallback-classloadstarted-method.md)|Upozorní profileru, že je načtena třída.|  
|[ClassUnloadFinished – metoda](icorprofilercallback-classunloadfinished-method.md)|Upozorní profileru, že se dokončila uvolňování třídy.|  
|[ClassUnloadStarted – metoda](icorprofilercallback-classunloadstarted-method.md)|Upozorní profileru, že je uvolněna třída.|  
|[COMClassicVTableCreated – metoda](icorprofilercallback-comclassicvtablecreated-method.md)|Upozorní profileru, že se vytvořila obálka pro vyvolané za běhu (RCW) pro zadané IID a třídu.|  
|[COMClassicVTableDestroyed – metoda](icorprofilercallback-comclassicvtabledestroyed-method.md)|Upozorní profileru, že je zničena aplikace RCW.|  
|[ExceptionCatcherEnter – metoda](icorprofilercallback-exceptioncatcherenter-method.md)|Upozorňuje profileru, že řízení se předává příslušnému `catch` bloku.|  
|[ExceptionCatcherLeave – metoda](icorprofilercallback-exceptioncatcherleave-method.md)|Upozorňuje profileru, že řízení se předává z příslušného `catch` bloku.|  
|[ExceptionCLRCatcherExecute – metoda](icorprofilercallback-exceptionclrcatcherexecute-method.md)|Zastaralé v .NET Framework verze 2,0.|  
|[ExceptionCLRCatcherFound – metoda](icorprofilercallback-exceptionclrcatcherfound-method.md)|Zastaralé v .NET Framework 2,0.|  
|[ExceptionOSHandlerEnter – metoda](icorprofilercallback-exceptionoshandlerenter-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.|  
|[ExceptionOSHandlerLeave – metoda](icorprofilercallback-exceptionoshandlerleave-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravovaných výjimkách, musí tyto informace získat jiným způsobem.|  
|[ExceptionSearchCatcherFound – metoda](icorprofilercallback-exceptionsearchcatcherfound-method.md)|Upozorní profileru, že ve fázi hledání výjimek byla nalezena obslužná rutina pro vyvolanou výjimku.|  
|[ExceptionSearchFilterEnter – metoda](icorprofilercallback-exceptionsearchfilterenter-method.md)|Upozorní profileru, že je spuštěn filtr uživatele.|  
|[ExceptionSearchFilterLeave – metoda](icorprofilercallback-exceptionsearchfilterleave-method.md)|Upozorní profileru, že uživatel právě dokončil provádění filtru.|  
|[ExceptionSearchFunctionEnter – metoda](icorprofilercallback-exceptionsearchfunctionenter-method.md)|Upozorní profileru, že byla zadána funkce vyhledávací fáze zpracování výjimek.|  
|[ExceptionSearchFunctionLeave – metoda](icorprofilercallback-exceptionsearchfunctionleave-method.md)|Upozorní profileru, že prohledávání fáze zpracování výjimek dokončila hledání funkce.|  
|[ExceptionThrown – metoda](icorprofilercallback-exceptionthrown-method.md)|Upozorní profileru, že byla vyvolána výjimka.|  
|[ExceptionUnwindFinallyEnter – metoda](icorprofilercallback-exceptionunwindfinallyenter-method.md)|Upozorní profileru, že unwind fáze zpracování výjimek zadává `finally` klauzuli obsaženou v zadané funkci.|  
|[ExceptionUnwindFinallyLeave – metoda](icorprofilercallback-exceptionunwindfinallyleave-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek opustila `finally` klauzuli.|  
|[ExceptionUnwindFunctionEnter – metoda](icorprofilercallback-exceptionunwindfunctionenter-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek zavolala funkci.|  
|[ExceptionUnwindFunctionLeave – metoda](icorprofilercallback-exceptionunwindfunctionleave-method.md)|Upozorní profileru, že zpětná fáze zpracování výjimek dokončila odvinutí funkce.|  
|[FunctionUnloadStarted – metoda](icorprofilercallback-functionunloadstarted-method.md)|Upozorní profileru, že modul runtime zahájil uvolnění funkce.|  
|[Initialize – metoda](icorprofilercallback-initialize-method.md)|Volá se, aby se inicializoval Profiler při každém spuštění nové aplikace CLR.|  
|[JITCachedFunctionSearchFinished – metoda](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Upozorní profileru, že vyhledávání skončilo pro funkci, která byla zkompilována dříve pomocí nástroje NGen. exe.|  
|[JITCachedFunctionSearchStarted – metoda](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Upozorní profileru, že bylo spuštěno vyhledávání pro funkci, která byla dříve kompilována pomocí nástroje NGen. exe.|  
|[JITCompilationFinished – metoda](icorprofilercallback-jitcompilationfinished-method.md)|Upozorní profileru, že kompilátor JIT dokončil kompilaci funkce.|  
|[JITCompilationStarted – metoda](icorprofilercallback-jitcompilationstarted-method.md)|Upozorní profileru, že kompilátor JIT (just-in-time) začal kompilovat funkci.|  
|[JITFunctionPitched – metoda](icorprofilercallback-jitfunctionpitched-method.md)|Upozorní profileru, že byla z paměti odebrána funkce, která byla kompilována JIT.|  
|[JITInlining – metoda](icorprofilercallback-jitinlining-method.md)|Upozorní profileru, že se chystá kompilátor JIT Vložit funkci do řádku s jinou funkcí.|  
|[ManagedToUnmanagedTransition – metoda](icorprofilercallback-managedtounmanagedtransition-method.md)|Upozorní profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.|  
|[ModuleAttachedToAssembly – metoda](icorprofilercallback-moduleattachedtoassembly-method.md)|Upozorní profileru, že je modul připojen ke svému nadřazenému sestavení.|  
|[ModuleLoadFinished – metoda](icorprofilercallback-moduleloadfinished-method.md)|Upozorní profileru, že se dokončilo načítání modulu.|  
|[ModuleLoadStarted – metoda](icorprofilercallback-moduleloadstarted-method.md)|Upozorní profileru, že je modul načítán.|  
|[ModuleUnloadFinished – metoda](icorprofilercallback-moduleunloadfinished-method.md)|Upozorní profileru, že se dokončilo uvolňování modulu.|  
|[ModuleUnloadStarted – metoda](icorprofilercallback-moduleunloadstarted-method.md)|Upozorní profileru, že je modul uvolňován.|  
|[MovedReferences – metoda](icorprofilercallback-movedreferences-method.md)|Upozorní profiler na odkazy na objekty, které se přesunuly během uvolňování paměti.|  
|[ObjectAllocated – metoda](icorprofilercallback-objectallocated-method.md)|Upozorní profileru, že paměť v haldě byla přidělena pro objekt.|  
|[ObjectReferences – metoda](icorprofilercallback-objectreferences-method.md)|Upozorňuje Profiler na objekty v paměti, na které se odkazuje zadaný objekt.|  
|[ObjectsAllocatedByClass – metoda](icorprofilercallback-objectsallocatedbyclass-method.md)|Upozorňuje Profiler o počtu instancí každé zadané třídy, které byly vytvořeny od předchozí kolekce uvolnění paměti.|  
|[RemotingClientInvocationFinished – metoda](icorprofilercallback-remotingclientinvocationfinished-method.md)|Upozorní profileru, že volání vzdálené komunikace bylo dokončeno na straně klienta.|  
|[RemotingClientInvocationStarted – metoda](icorprofilercallback-remotingclientinvocationstarted-method.md)|Upozorní profileru, že bylo zahájeno volání vzdálené komunikace.|  
|[RemotingClientReceivingReply – metoda](icorprofilercallback-remotingclientreceivingreply-method.md)|Upozorní profileru, že je dokončena serverová část volání vzdálené komunikace a klient nyní přijímá a chystá zpracovat odpověď.|  
|[RemotingClientSendingMessage – metoda](icorprofilercallback-remotingclientsendingmessage-method.md)|Upozorní profileru, že klient posílá požadavek na server.|  
|[RemotingServerInvocationReturned – metoda](icorprofilercallback-remotingserverinvocationreturned-method.md)|Upozorní profileru, že proces skončil voláním metody v reakci na požadavek na vyvolání vzdálené metody.|  
|[RemotingServerInvocationStarted – metoda](icorprofilercallback-remotingserverinvocationstarted-method.md)|Upozorní profileru, že proces vyvolává volání metody v reakci na požadavek na vyvolání vzdálené metody.|  
|[RemotingServerReceivingMessage – metoda](icorprofilercallback-remotingserverreceivingmessage-method.md)|Upozorní profileru, že proces přijímá volání vzdálené metody nebo žádost o aktivaci.|  
|[RemotingServerSendingReply – metoda](icorprofilercallback-remotingserversendingreply-method.md)|Upozorní profileru, že proces dokončil zpracování žádosti o vyvolání vzdálené metody a chystá se odeslat odpověď prostřednictvím kanálu.|  
|[RootReferences – metoda](icorprofilercallback-rootreferences-method.md)|Oznamuje profileru informace o kořenových odkazech po uvolnění paměti.|  
|[RuntimeResumeFinished – metoda](icorprofilercallback-runtimeresumefinished-method.md)|Upozorní profileru, že modul runtime obnovil všechna běhová vlákna a vrátil se do normálního provozu.|  
|[RuntimeResumeStarted – metoda](icorprofilercallback-runtimeresumestarted-method.md)|Upozorní profileru, že modul runtime obnovuje všechna běhová vlákna.|  
|[RuntimeSuspendAborted – metoda](icorprofilercallback-runtimesuspendaborted-method.md)|Upozorní profileru, že modul runtime přerušil přerušení běhu, ke kterému došlo.|  
|[RuntimeSuspendFinished – metoda](icorprofilercallback-runtimesuspendfinished-method.md)|Upozorní profileru, že modul runtime dokončil pozastavení všech vláken za běhu.|  
|[RuntimeSuspendStarted – metoda](icorprofilercallback-runtimesuspendstarted-method.md)|Upozorní profileru, že modul runtime se chystá pozastavit všechna vlákna za běhu.|  
|[RuntimeThreadResumed – metoda](icorprofilercallback-runtimethreadresumed-method.md)|Upozorní profileru, že zadané vlákno bylo po pozastavení obnoveno.|  
|[RuntimeThreadSuspended – metoda](icorprofilercallback-runtimethreadsuspended-method.md)|Upozorní profileru, že zadané vlákno bylo nebo bude pozastaveno.|  
|[Shutdown – metoda](icorprofilercallback-shutdown-method.md)|Oznamuje profileru, že se aplikace vypíná.|  
|[ThreadAssignedToOSThread – metoda](icorprofilercallback-threadassignedtoosthread-method.md)|Upozorní profileru, že spravované vlákno je implementováno pomocí konkrétního vlákna operačního systému (OS).|  
|[ThreadCreated – metoda](icorprofilercallback-threadcreated-method.md)|Upozorní profileru, že bylo vytvořeno vlákno.|  
|[ThreadDestroyed – metoda](icorprofilercallback-threaddestroyed-method.md)|Upozorní profileru, že došlo ke zničení vlákna.|  
|[UnmanagedToManagedTransition – metoda](icorprofilercallback-unmanagedtomanagedtransition-method.md)|Upozorní profileru, že došlo k přechodu z nespravovaného kódu do spravovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` rozhraní (nebo [ICorProfilerCallback2](icorprofilercallback2-interface.md)) pro oznámení profileru, když dojde k odběru události, ke které má Profiler odběr. Toto je primární rozhraní zpětného volání, přes které CLR komunikuje s profilerem kódu.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro .NET Framework verze 2,0 nebo novější musí Profiler také implementovat `ICorProfilerCallback2` metody. Každá implementace metody musí vracet hodnotu HRESULT, která má hodnotu S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md).  
  
 V registru systému Microsoft Windows musí Profiler kódu zaregistrovat svůj objekt modelu COM (Component Object Model), který implementuje `ICorProfilerCallback` rozhraní a `ICorProfilerCallback2` . Profiler kódu se přihlašuje k odběru událostí, ke kterým chce dostávat oznámení voláním [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)v profileru. Profiler je pak schopný přijímat oznámení z modulu runtime, když dojde k události, která se chystá, nebo k ní došlo pouze v průběhu provádění procesu modulu runtime.  
  
> [!NOTE]
> Profiler registruje jeden objekt COM. Pokud je profiler cílen na .NET Framework verze 1,0 nebo 1,1, musí tento objekt COM implementovat pouze metody `ICorProfilerCallback` . Pokud cílí na .NET Framework verze 2,0 nebo novější, musí objekt COM také implementovat metody `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 – rozhraní](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
