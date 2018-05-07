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
ms.openlocfilehash: 96c8c9de7a6b26c9a00a0ffaf4fb50c08a80d5a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback – rozhraní
Poskytuje metody, které jsou používány common language runtime (CLR) profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AppDomainCreationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Upozorní profileru vytvořený domény aplikace.|  
|[AppDomainCreationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Upozorní profileru se vytváří doménu aplikace.|  
|[AppDomainShutdownFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Upozorní profileru, že domény aplikace byl odpojen z procesu.|  
|[AppDomainShutdownStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Upozorní profileru, že domény aplikace odpojení z procesu.|  
|[AssemblyLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Upozorní profileru, že sestavení dokončil načítání.|  
|[AssemblyLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Upozorní profileru se načítá sestavení.|  
|[AssemblyUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Upozorní profileru sestavení byl odpojen.|  
|[AssemblyUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Upozorní profileru odpojení sestavení.|  
|[ClassLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Upozorní profileru, že třídu dokončil načítání.|  
|[ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Upozorní profileru, že třída je právě načítán.|  
|[ClassUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Upozorní profileru, že byla dokončena třídu uvolnění.|  
|[ClassUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Odpojení třídy upozorní profileru.|  
|[COMClassicVTableCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Vytvořený obálka volatelná za běhu (RCW) pro zadaný identifikátor IID a třída upozorní profileru.|  
|[COMClassicVTableDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Je zničen RCW upozorní profileru.|  
|[ExceptionCatcherEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Upozorní profileru, který je předáván ovládacího prvku na příslušné `catch` bloku.|  
|[ExceptionCatcherLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Upozorní profileru, který ovládací prvek je předávána mimo odpovídající `catch` bloku.|  
|[ExceptionCLRCatcherExecute – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Zastaralé v rozhraní .NET Framework verze 2.0.|  
|[ExceptionCLRCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Zastaralé v rozhraní .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Není implementováno. Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[ExceptionOSHandlerLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Není implementováno. Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[ExceptionSearchCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Upozorní profileru, že vyhledávání fáze zpracování výjimky má umístěný obslužnou rutinu pro výjimku, která byla vyvolána.|  
|[ExceptionSearchFilterEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Upozorní profileru, že se spouští filtr uživatelů.|  
|[ExceptionSearchFilterLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Upozorní profileru, že filtr uživatelů se právě dokončila spuštění.|  
|[ExceptionSearchFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Upozorní profileru, že fázi vyhledávání výjimek zadal funkce.|  
|[ExceptionSearchFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Upozorní profileru, že prohledávání funkce vyhledávání fáze zpracování výjimky bylo dokončeno.|  
|[ExceptionThrown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Upozorní profileru, že byla vyvolána výjimka.|  
|[ExceptionUnwindFinallyEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Upozorní profileru, který fázi unwind výjimky je zpracování zadání `finally` klauzule obsažené v zadanou funkci.|  
|[ExceptionUnwindFinallyLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Upozorní profileru, který fázi unwind výjimky zpracování opustil `finally` klauzule.|  
|[ExceptionUnwindFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Upozorní profileru, že fázi unwind výjimek zadal funkce.|  
|[ExceptionUnwindFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Upozorní profileru, že byla dokončena fázi unwind výjimek unwinding funkce.|  
|[FunctionUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Upozorní profileru, že modul runtime bylo zahájeno Unload funkce.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Volat za účelem inicializace profileru při každém spuštění nové aplikace CLR.|  
|[JITCachedFunctionSearchFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Upozorní profileru, že bylo dokončeno vyhledávání pro funkce, který byl kompilován s použitím dříve NGen.exe.|  
|[JITCachedFunctionSearchStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Upozorní profileru, že pro funkci, která byl kompilován s použitím dříve NGen.exe bylo zahájeno hledání.|  
|[JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Upozorní profileru, že kompilování funkce kompilátoru JIT byla dokončena.|  
|[JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna zkompilovat funkce.|  
|[JITFunctionPitched – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Upozorní profileru, funkce, které bylo kompilováno za běhu byl odebrán z paměti.|  
|[JITInlining – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Upozorní profileru, že kompilátoru za běhu se chystáte vložit funkci souladu jinou funkci.|  
|[ManagedToUnmanagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Upozorní profileru došlo k chybě přechod ze spravovaného kódu na nespravovaný kód.|  
|[ModuleAttachedToAssembly – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Upozorní profileru, že se modul připojen k její nadřazené sestavení.|  
|[ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Aby modul dokončil načítání upozorní profileru.|  
|[ModuleLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Aby modul načítá upozorní profileru.|  
|[ModuleUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Aby modul dokončil uvolnění upozorní profileru.|  
|[ModuleUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Upozorní profileru odpojení modulu.|  
|[MovedReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Upozorní profileru o odkazy na objekty, které byly přesunuty během uvolňování paměti.|  
|[ObjectAllocated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Upozorní profileru, která se přidělí paměť v rámci haldy pro objekt.|  
|[ObjectReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Upozorní profileru o objektech v paměti odkazuje zadaný objekt.|  
|[ObjectsAllocatedByClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od předchozí uvolňování profileru.|  
|[RemotingClientInvocationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Jestli volání vzdálené komunikace spustila dokončení v klientském počítači upozorní profileru.|  
|[RemotingClientInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Aby bylo zahájeno vzdáleného volání upozorní profileru.|  
|[RemotingClientReceivingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Upozorní profileru, který na straně serveru část vzdáleného volání bylo dokončeno a klient nyní získává a rozhodli jste se zpracovat odpověď.|  
|[RemotingClientSendingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Upozorní profileru, že klient odesílá požadavek na server.|  
|[RemotingServerInvocationReturned – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Upozorní profileru, že proces dokončení volání metody v reakci na žádost o volání vzdálené metody.|  
|[RemotingServerInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Upozorní profileru, že je proces vyvolání metody v reakci na žádost o volání vzdálené metody.|  
|[RemotingServerReceivingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Upozorní profileru, že proces přijímá žádost o vzdálené metody vyvolání nebo aktivace.|  
|[RemotingServerSendingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profileru upozorní, že proces dokončení zpracování požadavku volání vzdálené metody a má přenášet odpověď prostřednictvím kanálu.|  
|[RootReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Upozorní profileru s informacemi o odkazů na kořenový po uvolnění paměti.|  
|[RuntimeResumeFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profileru upozorní, že modul runtime obnovil všechna vlákna modulu runtime a vrátila do normálního provozu.|  
|[RuntimeResumeStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Upozorní profileru, že modul runtime obnovuje všechna vlákna běhu.|  
|[RuntimeSuspendAborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Aby modul runtime přerušil pozastavení runtime, který došlo ke upozorní profileru.|  
|[RuntimeSuspendFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Upozorní profileru, modul runtime byla dokončena pozastavení všechna vlákna běhu.|  
|[RuntimeSuspendStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Upozorní profileru, že běhové prostředí se chystá pozastavit všechna vlákna běhu.|  
|[RuntimeThreadResumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Upozorní profileru, že zadaný vlákno obnovil po bylo pozastaveno.|  
|[RuntimeThreadSuspended – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Profileru upozorní, že byl zadaný vlákno, nebo se chystáte, pozastaví.|  
|[Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Aby se aplikace vypíná upozorní profileru.|  
|[ThreadAssignedToOSThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Upozorní profileru, že spravované vlákno se implementuje pomocí vlákno konkrétní operační systém (OS).|  
|[ThreadCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Upozorní profileru vytvořený vlákna.|  
|[ThreadDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Upozorní profileru, byl zničen vlákna.|  
|[UnmanagedToManagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Upozorní profileru došlo k chybě přechod z nespravovaného kódu do spravovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá metodu `ICorProfilerCallback` (nebo [icorprofilercallback2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) rozhraní oznámit profileru události, ke kterému se připojila profileru, když dojde k. Toto je primární zpětného volání rozhraní, pomocí kterého modulu CLR komunikuje s profileru kódu.  
  
 Kód profileru musí implementovat metody `ICorProfilerCallback` rozhraní. Pro rozhraní .NET Framework verze 2.0 nebo novější, musíte také implementovat profileru `ICorProfilerCallback2` metody. Každá metoda implementace musí vracet HRESULT s hodnotou S_OK v případě úspěchu nebo E_FAIL při selhání. V současné době modulu CLR ignoruje HRESULT, který se vrátí po každé zpětné volání s výjimkou [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 V registru systému Windows, musíte zaregistrovat kód profileru jeho objektu modelu COM (Component Object), který implementuje `ICorProfilerCallback` a `ICorProfilerCallback2` rozhraní. Kód profileru přihlásí k událostem, pro které chce dostávat oznámení voláním [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci profileru [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profileru je pak může přijímat oznámení z modulu runtime, když událost dojde nebo došlo k jenom v provádění procesu modulu runtime.  
  
> [!NOTE]
>  Profileru zaregistruje jednoho objektu COM. Pokud je profileru cílení na rozhraní .NET Framework verze 1.0 a 1.1, že objekt COM musí implementovat jenom metody `ICorProfilerCallback`. Pokud je cílení na rozhraní .NET Framework verze 2.0 nebo novější, objekt COM musí implementovat metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
