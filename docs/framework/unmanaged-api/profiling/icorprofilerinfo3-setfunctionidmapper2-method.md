---
title: ICorProfilerInfo3::SetFunctionIDMapper2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 2c06b9b7933245dc0e69e430a3fe4a515f8a50f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449576"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 – metoda
Určuje funkci implementovanou profilerem, která bude volána k namapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru. Tato metoda rozšiřuje metodu [ICorProfilerInfo:: SetFunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) s parametrem další dat, který profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunc`  
 pro Ukazatel na implementaci [FunctionIDMapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) , která bude volána pro mapování `FunctionID`ch hodnot na jejich alternativní hodnoty.  
  
 `clientData`  
 pro Ukazatel, který je předán všem voláním funkce [FunctionIDMapper2 –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) provedeným aktuálním modulem runtime. Profiler může tyto informace použít k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Alternativy hodnot FunctionID budou předány příjezdce a ukončení funkce profileru ([FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md); nebo [FunctionEnter3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)), které jsou určeny metodou [SetEnterLeaveFunctionHooks3 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [SetEnterLeaveFunctionHooks3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .  
  
 Metodu `FunctionIDMapper2` lze nastavit pouze jednou. Doporučujeme, abyste ji nastavili ve zpětném volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [SetFunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
