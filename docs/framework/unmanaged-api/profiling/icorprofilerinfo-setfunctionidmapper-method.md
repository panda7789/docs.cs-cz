---
title: ICorProfilerInfo::SetFunctionIDMapper – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 4ba3c378b93e3ae1ef288c0edabfacfcfd7070d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438675"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper – metoda
Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunc`  
 pro Ukazatel na implementaci [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) , která bude volána pro mapování `FunctionID`ch hodnot na jejich alternativní hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Alternativy `FunctionID`ch hodnot budou předány příjezdce a ukončení funkce profileru ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)a [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)), které jsou určeny metodou [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .  
  
 `FunctionIDMapper` lze nastavit pouze jednou a je doporučeno ji nastavit ve zpětném volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
