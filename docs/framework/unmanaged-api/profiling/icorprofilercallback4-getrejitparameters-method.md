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
ms.openlocfilehash: 527e48d02d5267d6ae41214686c2e8c997d85dca
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499542"
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
 pro `MethodDef`Metoda, pro kterou modul CLR potřebuje parametry rekompilace JIT.  
  
 `pFunctionControl`  
 pro Ukazatel na rozhraní [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , které může Profiler použít k poskytnutí informací o rekompilaci JIT pro metodu, která je právě zkompilována.  
  
## <a name="remarks"></a>Poznámky  
 CLR vyvolá `GetReJITParameters` zpětné volání, aby Profiler mohl určit parametry pro opětovné zkompilování dané metody. `GetReJITParameters`Zpětné volání je vystaveno pouze jednou funkcí. parametry zadané profilerem platí pro všechny instance této funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [JITCompilationStarted – metoda](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted – metoda](icorprofilercallback4-rejitcompilationstarted-method.md)
