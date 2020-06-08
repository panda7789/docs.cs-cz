---
title: ICorProfilerCallback::Shutdown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503176"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown – metoda
Oznamuje profileru, že se aplikace vypíná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru nemůže bezpečně volat metody rozhraní [ICorProfilerInfo](icorprofilerinfo-interface.md) po `Shutdown` volání metody. Jakákoli volání `ICorProfilerInfo` metod způsobí nedefinované chování poté, co `Shutdown` Metoda vrátí. K určitým neměnným událostem může docházet i po vypnutí. Profiler by měl být při výskytu okamžitě vrácen.  
  
 `Shutdown`Metoda bude volána pouze v případě, že je spravovaná aplikace, která je profilovaná, spuštěna jako spravovaný kód (to znamená, že počáteční rámec v zásobníku procesu je spravovaný). Pokud se aplikace spustila jako nespravovaný kód, ale později se přeskočí do spravovaného kódu, vytvoří se instance modulu CLR (Common Language Runtime), pak `Shutdown` se nebude volat. V těchto případech by měl Profiler do knihovny zahrnout `DllMain` rutinu, která používá hodnotu DLL_PROCESS_DETACH k uvolnění prostředků a k vyčištění zpracování dat, jako je například vyprazdňování trasování na disk a tak dále.  
  
 Obecně platí, že Profiler se musí vypořádat s neočekávanými vypnutími. Například proces může být zastaven `TerminateProcess` metodou Win32's (deklarovaným v Winbase. h). V ostatních případech CLR zachová určitá spravovaná vlákna (vlákna na pozadí), aniž by pro ně musela doručovat zprávy s řazením.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [Initialize – metoda](icorprofilercallback-initialize-method.md)
