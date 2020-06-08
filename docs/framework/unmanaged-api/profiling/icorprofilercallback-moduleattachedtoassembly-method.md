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
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503390"
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
 Modul lze načíst prostřednictvím tabulky importních adres (IAT), prostřednictvím volání `LoadLibrary` nebo prostřednictvím odkazu na metadata. V důsledku toho má zavaděč modulu CLR (Common Language Runtime) více cest kódu pro určení sestavení, ve kterém modul žije. Proto je možné, že po volání metody [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) modul neví, v jakém sestavení je, a získat ID nadřazeného sestavení není možné. `ModuleAttachedToAssembly`Metoda je volána, když je modul připojen ke svému nadřazenému sestavení a lze získat jeho nadřazené ID sestavení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
