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
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446940"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown – metoda
Oznamuje profileru, že se aplikace vypíná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód profileru nemůže bezpečně volat metody rozhraní [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) po volání metody `Shutdown`. Jakákoli volání metod `ICorProfilerInfo` způsobí nedefinované chování po návratu metody `Shutdown`. K určitým neměnným událostem může docházet i po vypnutí. Profiler by měl být při výskytu okamžitě vrácen.  
  
 Metoda `Shutdown` bude volána pouze v případě, že je spravovaná aplikace, která je profilovaná, spuštěná jako spravovaný kód (tj. počáteční rámec na zásobníku procesu je spravovaný). Pokud se aplikace spustila jako nespravovaný kód, ale později se přeskočí do spravovaného kódu, vytvoří se instance modulu CLR (Common Language Runtime), a poté `Shutdown` nebude volána. V těchto případech by měl Profiler ve své knihovně zahrnovat `DllMain` rutinu, která používá hodnotu DLL_PROCESS_DETACH k uvolnění prostředků a k vyčištění zpracování dat, jako je například vyprazdňování trasování na disk a tak dále.  
  
 Obecně platí, že Profiler se musí vypořádat s neočekávanými vypnutími. Například proces může být zastaven metodou Win32's `TerminateProcess` (deklarovaným v Winbase. h). V ostatních případech CLR zachová určitá spravovaná vlákna (vlákna na pozadí), aniž by pro ně musela doručovat zprávy s řazením.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
