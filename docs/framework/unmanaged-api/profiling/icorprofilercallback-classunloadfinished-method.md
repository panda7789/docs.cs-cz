---
title: ICorProfilerCallback::ClassUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500374"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>ICorProfilerCallback::ClassUnloadFinished – metoda
Upozorní profileru, že se dokončila uvolňování třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `classId`

  \[v] identifikuje třídu, která byla uvolněna.

- `hrStatus`

  \[in] HRESULT, který označuje, zda byla třída úspěšně uvolněna.
  
## <a name="remarks"></a>Poznámky  
 Některé části uvolňování třídy mohou pokračovat po `ClassUnloadFinished` zpětném volání. Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání. Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování třídy byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ClassUnloadStarted – metoda](icorprofilercallback-classunloadstarted-method.md)
