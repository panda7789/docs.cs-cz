---
title: ICorProfilerCallback::ModuleUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8dd5e2ecf22ce14765df8972611f1f95109f76ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769201"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a>ICorProfilerCallback::ModuleUnloadFinished – metoda
Upozorní profiler modulu dokončení uvolnění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] ID modulu, který byl odpojen.  
  
 `hrStatus`  
 [in] HRESULT, která určuje, zda modul byl uvolněn úspěšně.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `moduleId` není platná pro požadavek informace po [icorprofilercallback::moduleunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) metoda vrátí hodnotu.  
  
 Některé části uvolnění třídy může pokračovat po `ModuleUnloadFinished` zpětného volání. Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu. Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění modulu proběhla úspěšně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
