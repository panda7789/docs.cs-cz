---
title: ICorProfilerCallback::JITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 0da67f0d4be779cc21481d03a21209620289888e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500052"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished – metoda
Upozorní profileru, že kompilátor JIT (just-in-time) dokončil kompilaci funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[v] ID funkce, která byla zkompilována.

- `hrStatus`

  \[in] hodnota označující, zda byla kompilace úspěšná.

- `fIsSafeToBlock`

  \[in] hodnota, která označuje Profiler, zda bude blokování ovlivněno operací modulu runtime. Hodnota je, `true` Pokud blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. v opačném případě `false` .

  I když hodnota `true` nebude mít vliv na modul runtime, může zkosit výsledky profilace.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [JITCompilationStarted – metoda](icorprofilercallback-jitcompilationstarted-method.md)
