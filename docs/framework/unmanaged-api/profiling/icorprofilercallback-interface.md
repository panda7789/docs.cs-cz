---
title: "ICorProfilerCallback – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback
helpviewer_keywords: ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type: apiref
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3370dade937d67aa40be263faf3a433d142d932c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback – rozhraní
Poskytuje metody, které jsou používány common language runtime (CLR) profileru kód upozornit, když dojde k události, ke kterým se připojila profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Appdomaincreationfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Upozorní profileru vytvořený domény aplikace.|  
|[Appdomaincreationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Upozorní profileru se vytváří doménu aplikace.|  
|[Appdomainshutdownfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Upozorní profileru, že domény aplikace byl odpojen z procesu.|  
|[Appdomainshutdownstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Upozorní profileru, že domény aplikace odpojení z procesu.|  
|[Assemblyloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Upozorní profileru, že sestavení dokončil načítání.|  
|[Assemblyloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Upozorní profileru se načítá sestavení.|  
|[Assemblyunloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Upozorní profileru sestavení byl odpojen.|  
|[Assemblyunloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Upozorní profileru odpojení sestavení.|  
|[Classloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Upozorní profileru, že třídu dokončil načítání.|  
|[Classloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Upozorní profileru, že třída je právě načítán.|  
|[Classunloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Upozorní profileru, že byla dokončena třídu uvolnění.|  
|[Classunloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Odpojení třídy upozorní profileru.|  
|[Comclassicvtablecreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Vytvořený obálka volatelná za běhu (RCW) pro zadaný identifikátor IID a třída upozorní profileru.|  
|[Comclassicvtabledestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Je zničen RCW upozorní profileru.|  
|[Exceptioncatcherenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Upozorní profileru, který je předáván ovládacího prvku na příslušné `catch` bloku.|  
|[Exceptioncatcherleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Upozorní profileru, který ovládací prvek je předávána mimo odpovídající `catch` bloku.|  
|[Exceptionclrcatcherexecute – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Zastaralé v rozhraní .NET Framework verze 2.0.|  
|[Exceptionclrcatcherfound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Zastaralé v rozhraní .NET Framework 2.0.|  
|[Exceptionoshandlerenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Není implementováno. Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[Exceptionoshandlerleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Není implementováno. Profileru, který vyžaduje informace o nespravované výjimky, musíte získat tyto informace jinými způsoby.|  
|[Exceptionsearchcatcherfound – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Upozorní profileru, že vyhledávání fáze zpracování výjimky má umístěný obslužnou rutinu pro výjimku, která byla vyvolána.|  
|[Exceptionsearchfilterenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Upozorní profileru, že se spouští filtr uživatelů.|  
|[Exceptionsearchfilterleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Upozorní profileru, že filtr uživatelů se právě dokončila spuštění.|  
|[Exceptionsearchfunctionenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Upozorní profileru, že fázi vyhledávání výjimek zadal funkce.|  
|[Exceptionsearchfunctionleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Upozorní profileru, že prohledávání funkce vyhledávání fáze zpracování výjimky bylo dokončeno.|  
|[Exceptionthrown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Upozorní profileru, že byla vyvolána výjimka.|  
|[Exceptionunwindfinallyenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Upozorní profileru, který fázi unwind výjimky je zpracování zadání `finally` klauzule obsažené v zadanou funkci.|  
|[Exceptionunwindfinallyleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Upozorní profileru, který fázi unwind výjimky zpracování opustil `finally` klauzule.|  
|[Exceptionunwindfunctionenter – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Upozorní profileru, že fázi unwind výjimek zadal funkce.|  
|[Exceptionunwindfunctionleave – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Upozorní profileru, že byla dokončena fázi unwind výjimek unwinding funkce.|  
|[Functionunloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Upozorní profileru, že modul runtime bylo zahájeno Unload funkce.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Volat za účelem inicializace profileru při každém spuštění nové aplikace CLR.|  
|[Jitcachedfunctionsearchfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Upozorní profileru, že bylo dokončeno vyhledávání pro funkce, který byl kompilován s použitím dříve NGen.exe.|  
|[Jitcachedfunctionsearchstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Upozorní profileru, že pro funkci, která byl kompilován s použitím dříve NGen.exe bylo zahájeno hledání.|  
|[Jitcompilationfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Upozorní profileru, že kompilování funkce kompilátoru JIT byla dokončena.|  
|[Jitcompilationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna zkompilovat funkce.|  
|[Jitfunctionpitched – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Upozorní profileru, funkce, které bylo kompilováno za běhu byl odebrán z paměti.|  
|[Jitinlining – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Upozorní profileru, že kompilátoru za běhu se chystáte vložit funkci souladu jinou funkci.|  
|[Managedtounmanagedtransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Upozorní profileru došlo k chybě přechod ze spravovaného kódu na nespravovaný kód.|  
|[Moduleattachedtoassembly – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Upozorní profileru, že se modul připojen k její nadřazené sestavení.|  
|[Moduleloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Aby modul dokončil načítání upozorní profileru.|  
|[Moduleloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Aby modul načítá upozorní profileru.|  
|[Moduleunloadfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Aby modul dokončil uvolnění upozorní profileru.|  
|[Moduleunloadstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Upozorní profileru odpojení modulu.|  
|[Movedreferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Upozorní profileru o odkazy na objekty, které byly přesunuty během uvolňování paměti.|  
|[Objectallocated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Upozorní profileru, která se přidělí paměť v rámci haldy pro objekt.|  
|[ObjectReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Upozorní profileru o objektech v paměti odkazuje zadaný objekt.|  
|[Objectsallocatedbyclass – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od předchozí uvolňování profileru.|  
|[Remotingclientinvocationfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Jestli volání vzdálené komunikace spustila dokončení v klientském počítači upozorní profileru.|  
|[Remotingclientinvocationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Aby bylo zahájeno vzdáleného volání upozorní profileru.|  
|[Remotingclientreceivingreply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Upozorní profileru, který na straně serveru část vzdáleného volání bylo dokončeno a klient nyní získává a rozhodli jste se zpracovat odpověď.|  
|[Remotingclientsendingmessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Upozorní profileru, že klient odesílá požadavek na server.|  
|[Remotingserverinvocationreturned – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Upozorní profileru, že proces dokončení volání metody v reakci na žádost o volání vzdálené metody.|  
|[Remotingserverinvocationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Upozorní profileru, že je proces vyvolání metody v reakci na žádost o volání vzdálené metody.|  
|[Remotingserverreceivingmessage – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Upozorní profileru, že proces přijímá žádost o vzdálené metody vyvolání nebo aktivace.|  
|[Remotingserversendingreply – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profileru upozorní, že proces dokončení zpracování požadavku volání vzdálené metody a má přenášet odpověď prostřednictvím kanálu.|  
|[Rootreferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Upozorní profileru s informacemi o odkazů na kořenový po uvolnění paměti.|  
|[Runtimeresumefinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profileru upozorní, že modul runtime obnovil všechna vlákna modulu runtime a vrátila do normálního provozu.|  
|[Runtimeresumestarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Upozorní profileru, že modul runtime obnovuje všechna vlákna běhu.|  
|[Runtimesuspendaborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Aby modul runtime přerušil pozastavení runtime, který došlo ke upozorní profileru.|  
|[Runtimesuspendfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Upozorní profileru, modul runtime byla dokončena pozastavení všechna vlákna běhu.|  
|[Runtimesuspendstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Upozorní profileru, že běhové prostředí se chystá pozastavit všechna vlákna běhu.|  
|[Runtimethreadresumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Upozorní profileru, že zadaný vlákno obnovil po bylo pozastaveno.|  
|[Runtimethreadsuspended – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Profileru upozorní, že byl zadaný vlákno, nebo se chystáte, pozastaví.|  
|[Shutdown – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Aby se aplikace vypíná upozorní profileru.|  
|[Threadassignedtoosthread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Upozorní profileru, že spravované vlákno se implementuje pomocí vlákno konkrétní operační systém (OS).|  
|[Threadcreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Upozorní profileru vytvořený vlákna.|  
|[Threaddestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Upozorní profileru, byl zničen vlákna.|  
|[Unmanagedtomanagedtransition – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Upozorní profileru došlo k chybě přechod z nespravovaného kódu do spravovaného kódu.|  
  
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Icorprofilercallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Icorprofilercallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [Icorprofilercallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
