---
title: ICorProfilerCallback::AssemblyUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a75d31f0a2c844895363bb4693dbcb5aba4cce1f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775504"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished – metoda
Oznámí profileru, že sestavení byl uvolněn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Určuje sestavení, které uvolňován.  
  
 `hrStatus`  
 [in] HRESULT, která určuje, zda bylo sestavení úspěšně odpojen.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek informace po [icorprofilercallback::assemblyunloadstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda vrátí hodnotu.  
  
 Některé části uvolňování sestavení může pokračovat po `AssemblyUnloadFinished` zpětného volání. Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu. Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolňování sestavení byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
