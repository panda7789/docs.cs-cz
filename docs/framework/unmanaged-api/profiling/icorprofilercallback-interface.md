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
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598075"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback – rozhraní
Poskytuje metody, které se používají modulem common language runtime (CLR) pro oznámení profileru kód, pokud dojde k událostem, ke kterým se připojila profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AppDomainCreationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Upozornění profileru vytvoření domény aplikace.|  
|[AppDomainCreationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Oznámí profileru, že se vytváří domény aplikace.|  
|[AppDomainShutdownFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Oznámí profileru, že byl odpojen od procesu domény aplikace.|  
|[AppDomainShutdownStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Oznámí profileru, že se z procesu uvolnění domény aplikace.|  
|[AssemblyLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Oznámí profileru, že sestavení bylo dokončeno načítání.|  
|[AssemblyLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Načtení sestavení oznámí profileru.|  
|[AssemblyUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Oznámí profileru, že sestavení byl uvolněn.|  
|[AssemblyUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Oznámí profileru, že je sestavení uvolňován.|  
|[ClassLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Třída dokončení načítání oznámí profileru.|  
|[ClassLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Načtení třídy oznámí profileru.|  
|[ClassUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Třída dokončení uvolnění oznámí profileru.|  
|[ClassUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Oznámí profileru, že třída uvolňován.|  
|[COMClassicVTableCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Oznámí profileru, že se vytvořil obálka volatelná za běhu (RCW) pro zadaný identifikátor IID a třídy.|  
|[COMClassicVTableDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Oznámí profileru, že se likviduje obálky RCW.|  
|[ExceptionCatcherEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Oznámí profileru, který ovládací prvek je předávaný do příslušné `catch` bloku.|  
|[ExceptionCatcherLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Oznámí profileru, který se předává řízení mimo odpovídající `catch` bloku.|  
|[ExceptionCLRCatcherExecute – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Zastaralé v rozhraní .NET Framework verze 2.0.|  
|[ExceptionCLRCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Zastaralé v rozhraní .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[ExceptionOSHandlerLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Není implementováno. Profiler, který potřebuje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[ExceptionSearchCatcherFound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Oznámí profileru, že hledání fáze zpracování výjimek pružný obslužnou rutinu, která byla vyvolána výjimka.|  
|[ExceptionSearchFilterEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Oznámí profileru, že filtr uživatelů se zpracovává.|  
|[ExceptionSearchFilterLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Oznámí profileru, že filtr uživatelů jenom neskončí.|  
|[ExceptionSearchFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Oznámí profileru, že hledání fáze zpracování výjimek se dostala funkce.|  
|[ExceptionSearchFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Oznámí profileru, že hledání fáze zpracování výjimek dokončil vyhledávání funkce.|  
|[ExceptionThrown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Oznámí profileru, že byla vyvolána výjimka.|  
|[ExceptionUnwindFinallyEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Oznámí profileru, který fáze unwind výjimek zpracování přechází `finally` doložky zadanou funkci.|  
|[ExceptionUnwindFinallyLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Oznámí profileru, který fáze unwind výjimek zpracování není dostupný `finally` klauzuli.|  
|[ExceptionUnwindFunctionEnter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Oznámí profileru, že unwind fáze zpracování výjimek přešla na funkci.|  
|[ExceptionUnwindFunctionLeave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Unwind fáze zpracování výjimek dokončení uvolnění funkce oznámí profileru.|  
|[FunctionUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Oznámí profileru, modul runtime byla spuštěna uvolnit funkci.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Volá se, aby při každém spuštění nové aplikace CLR inicializaci profileru.|  
|[JITCachedFunctionSearchFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Dokončení vyhledávání pro funkci, která se zkompilovala dříve pomocí NGen.exe oznámí profileru.|  
|[JITCachedFunctionSearchStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Oznámí profileru, pro funkci, která se zkompilovala dříve pomocí NGen.exe bylo zahájeno hledání.|  
|[JITCompilationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Oznámí profileru, že byla dokončena kompilátor JIT kompilaci funkce.|  
|[JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Oznámí profileru, kompilátor just-in-time (JIT) byla spuštěna kompilovat funkci.|  
|[JITFunctionPitched – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Oznámí profileru, že funkce, který byl zkompilován JIT Kompilátorem byla odebrána z paměti.|  
|[JITInlining – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Oznámí profileru, že kompilátor JIT Chystáte se vložit funkci v jiné funkci.|  
|[ManagedToUnmanagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Oznámí profileru, že došlo k přechodu ze spravovaného kódu do nespravovaného kódu.|  
|[ModuleAttachedToAssembly – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Oznámí profileru, že se modul připojen k její nadřazené sestavení.|  
|[ModuleLoadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Upozorní profiler modulu dokončení načítání.|  
|[ModuleLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Oznámí profileru, načtení modulu.|  
|[ModuleUnloadFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Upozorní profiler modulu dokončení uvolnění.|  
|[ModuleUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Upozornění profileru uvolnění modulu.|  
|[MovedReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Upozornění profileru o odkazy na objekty, které byly přesunuty během uvolňování paměti.|  
|[ObjectAllocated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Oznámí profileru, který se přidělí paměť v rámci haldy objekt.|  
|[ObjectReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Upozornění profileru o objektech v paměti odkazuje zadaný objekt.|  
|[ObjectsAllocatedByClass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Upozornění profileru o počet instancí každé zadané třídy, které byly vytvořeny od předchozí kolekce uvolnění paměti.|  
|[RemotingClientInvocationFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Oznámí profileru, že dokončení běh vzdálené volání na straně klienta.|  
|[RemotingClientInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Oznámí profileru, vzdálené volání byla spuštěna.|  
|[RemotingClientReceivingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Oznámí profileru, který je dokončená část vzdálené volání na straně serveru a nyní přijímá klienta a o zpracování odpovědi.|  
|[RemotingClientSendingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Oznámí profileru, že klient odesílá požadavek na server.|  
|[RemotingServerInvocationReturned – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Proces dokončení volání metody v reakci na žádost o vzdálené metody vyvolání upozornění profileru.|  
|[RemotingServerInvocationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Oznámí profileru, že proces je volání metody v reakci na žádost o vzdálené metody volání.|  
|[RemotingServerReceivingMessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Oznámí profileru, že proces přijímá vzdálené metody vyvolání či aktivačním požadavku.|  
|[RemotingServerSendingReply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profiler upozorní, že procesu bylo dokončeno zpracování požadavku volání vzdálené metody a je přenášet odpovědi prostřednictvím kanálu.|  
|[RootReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Upozornění profileru s informacemi o odkazů na kořenový po uvolňování paměti.|  
|[RuntimeResumeFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profiler upozorní, že modul runtime obnovila všechna vlákna modulu runtime a se vrátí do normálního provozu.|  
|[RuntimeResumeStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Oznámí profileru, že modul runtime obnovuje všemi vlákny za běhu.|  
|[RuntimeSuspendAborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Oznámí profileru, že modul runtime byla přerušena, které se vyskytují pozastavení běhu.|  
|[RuntimeSuspendFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Oznámí profileru, že modul runtime dokončil pozastavení všemi vlákny za běhu.|  
|[RuntimeSuspendStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Oznámí profileru, že modul runtime Chystáte se pozastavit všechna vlákna za běhu.|  
|[RuntimeThreadResumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Oznámí profileru, že zadaný podproces obnovila po pozastavuje.|  
|[RuntimeThreadSuspended – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Profiler upozorní, že byl zadaného vlákna, nebo mu vyprší, pozastaví.|  
|[Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Oznámí profileru, že se aplikace vypíná.|  
|[ThreadAssignedToOSThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Oznámí profileru, že spravovaným vláknem se implementuje pomocí konkrétní operační systém (OS) vlákno.|  
|[ThreadCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Oznámí profileru, že vlákno vytvořil.|  
|[ThreadDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Oznámí profileru, že došlo ke zničení vlákno.|  
|[UnmanagedToManagedTransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Oznámí profileru, že došlo k přechodu z nespravovaného kódu pro spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` (nebo [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) rozhraní pro oznámení profileru po události, ke kterému se připojila profileru, vyvolá. Toto je primární zpětného volání rozhraní, pomocí kterého CLR komunikuje s profileru kód.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro rozhraní .NET Framework verze 2.0 nebo novější, musíte také implementovat profiler `ICorProfilerCallback2` metody. Každá implementace metoda musí vracet HRESULT, který má hodnotu S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnota HRESULT, který je vrácený každou zpětného volání s výjimkou [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 V registru Windows Microsoft profiler kódu musí zaregistrovat jeho objekt modelu COM (Component Object), který implementuje `ICorProfilerCallback` a `ICorProfilerCallback2` rozhraní. Profiler kódu přihlásí se k odběru událostí, pro které chce přijmout oznámení voláním [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci profileru [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler je pak moci přijímat oznámení z modulu runtime při události dojde nebo došlo k právě v spuštěného procesu modulu runtime.  
  
> [!NOTE]
>  Profiler zaregistruje jeden objekt modelu COM. Pokud profiler je cílen na verzi rozhraní .NET Framework verze 1.0 nebo 1.1, že objekt modelu COM by měl provádět pouze metody `ICorProfilerCallback`. Pokud se zaměřujete na rozhraní .NET Framework verze 2.0 nebo novější, objektu COM musí také implementovat metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
