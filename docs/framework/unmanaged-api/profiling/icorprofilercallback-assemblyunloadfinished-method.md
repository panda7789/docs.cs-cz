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
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500413"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished – metoda
Upozorní profileru, že bylo sestavení uvolněno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `assemblyId`

  \[v] identifikuje sestavení, které je uvolněno.

- `hrStatus`

  \[in] HRESULT, který označuje, zda bylo sestavení uvolněno úspěšně.

## <a name="remarks"></a>Poznámky  
 Hodnota `assemblyId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: assemblyunloadstarted –](icorprofilercallback-assemblyunloadstarted-method.md) .  
  
 Některé části uvolňování sestavení mohou pokračovat po `AssemblyUnloadFinished` zpětném volání. Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání. Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování sestavení byla úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
