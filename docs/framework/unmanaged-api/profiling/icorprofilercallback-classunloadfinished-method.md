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
ms.openlocfilehash: b78d604a28ffe01000a763f7e0dd3c1630e2c186
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435923"
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
 `classId`  
 pro Identifikuje třídu, která byla uvolněna.  
  
 `hrStatus`  
 pro Hodnota HRESULT, která označuje, zda byla třída úspěšně uvolněna.  
  
## <a name="remarks"></a>Poznámky  
 Některé části uvolňování třídy mohou pokračovat po `ClassUnloadFinished` zpětného volání. Selhání HRESULT v `hrStatus` označuje selhání. Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování třídy byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ClassUnloadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
