---
title: ICorProfilerCallback::ModuleAttachedToAssembly – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: d229b530062d759ab270612fa70b1799acbcadbe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448073"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly – metoda
Upozorní profileru, že je modul připojen ke svému nadřazenému sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro ID modulu, který se připojuje  
  
 `AssemblyId`  
 pro ID nadřazeného sestavení, ke kterému je modul připojen  
  
## <a name="remarks"></a>Poznámky  
 Modul lze načíst prostřednictvím tabulky importních adres (IAT), prostřednictvím volání `LoadLibrary`nebo prostřednictvím odkazu na metadata. V důsledku toho má zavaděč modulu CLR (Common Language Runtime) více cest kódu pro určení sestavení, ve kterém modul žije. Proto je možné, že po volání metody [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) modul neví, v jakém sestavení je, a získat ID nadřazeného sestavení není možné. Metoda `ModuleAttachedToAssembly` je volána, když je modul připojen ke svému nadřazenému sestavení a lze získat jeho nadřazené ID sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
