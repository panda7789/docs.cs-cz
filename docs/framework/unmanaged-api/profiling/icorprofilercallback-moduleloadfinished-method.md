---
title: ICorProfilerCallback::ModuleLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 08fbf49e6944de4934a9fe7a960405ee96a7d8e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445935"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished – metoda
Upozorní profileru, že se dokončilo načítání modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro ID modulu, který dokončil načítání.  
  
 `hrStatus`  
 pro Hodnota HRESULT, která označuje, zda byl modul úspěšně načten.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `moduleId` není platná pro požadavek na informace, dokud není volána metoda `ModuleLoadFinished`.  
  
 Některé části načtení modulu můžou pokračovat i po `ModuleLoadFinished` zpětném volání. Selhání HRESULT v `hrStatus` označuje selhání. Úspěšnost HRESULT v `hrStatus` však znamená, že první část načtení modulu byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
