---
title: ICorProfilerCallback::AssemblyLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 33b72c8d089e5b335069fe465987086dfa1243bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445167"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished – metoda
Upozorní profileru, že bylo dokončeno načítání sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 pro Identifikuje sestavení, které bylo načteno.  
  
 `hrStatus`  
 pro Hodnota HRESULT, která označuje, zda bylo sestavení úspěšně načteno.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek na informace, dokud není volána metoda `AssemblyLoadFinished`.  
  
 Některé části načtení sestavení mohou pokračovat po `AssemblyLoadFinished` zpětného volání. Selhání HRESULT v `hrStatus` označuje selhání. Úspěšnost HRESULT v `hrStatus` však znamená, že první část načítání sestavení byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
