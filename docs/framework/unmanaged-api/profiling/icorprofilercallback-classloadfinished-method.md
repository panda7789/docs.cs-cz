---
title: ICorProfilerCallback::ClassLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500387"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished – metoda
Upozorní profileru, že se dokončilo načítání třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `classId`

  \[v] identifikuje třídu, která byla načtena.

- `hrStatus`

  \[in] HRESULT, který označuje, zda byla třída úspěšně načtena.

## <a name="remarks"></a>Poznámky  
 Hodnota `classId` není platná pro požadavek na informace, dokud `ClassLoadFinished` není volána metoda.  
  
 Některé části načtení třídy mohou pokračovat po `ClassLoadFinished` zpětném volání. Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání. Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část načtení třídy byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ClassLoadStarted – metoda](icorprofilercallback-classloadstarted-method.md)
