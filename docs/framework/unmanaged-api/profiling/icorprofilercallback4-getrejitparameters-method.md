---
title: ICorProfilerCallback4::GetReJITParameters – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865308"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters – metoda
Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 pro Modul obsahující metodu, pro kterou CLR potřebuje parametry rekompilace JIT.  
  
 `methodId`  
 pro `MethodDef` metody, pro kterou modul CLR potřebuje parametry rekompilace JIT.  
  
 `pFunctionControl`  
 pro Ukazatel na rozhraní [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , které může Profiler použít k poskytnutí informací o rekompilaci JIT pro metodu, která je právě zkompilována.  
  
## <a name="remarks"></a>Poznámky  
 CLR vydá `GetReJITParameters` zpětného volání, aby Profiler mohl určit parametry pro opětovné zkompilování dané metody. Zpětné volání `GetReJITParameters` je vystaveno pouze jednou pro funkci; parametry zadané profilerem se vztahují na všechny instance této funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [JITCompilationStarted – metoda](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted – metoda](icorprofilercallback4-rejitcompilationstarted-method.md)
