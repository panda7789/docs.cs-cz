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
ms.openlocfilehash: 723cb277a7df592e0494505018f7422e4e40f5f6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496149"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 – metoda
Určuje funkci implementovanou v profileru, která bude volána k mapování `FunctionID` hodnot na alternativní hodnoty, které jsou předány do vstupních a ukončovacích funkcí profileru. Tato metoda rozšiřuje metodu [ICorProfilerInfo:: SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md) s parametrem další dat, který profilery mohou použít k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunc`  
 pro Ukazatel na implementaci [FunctionIDMapper2 –](functionidmapper2-function.md) , která bude volána pro mapování `FunctionID` hodnot na jejich alternativní hodnoty.  
  
 `clientData`  
 pro Ukazatel, který je předán všem voláním funkce [FunctionIDMapper2 –](functionidmapper2-function.md) provedeným aktuálním modulem runtime. Profiler může tyto informace použít k jednoznačnému rozlišení mezi moduly runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
  
## <a name="remarks"></a>Poznámky  
 Alternativy hodnot FunctionID budou předány příjezdce a ukončení funkce profileru ([FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md); nebo [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [Functionleave3withinfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md)), které jsou určeny metodou [SetEnterLeaveFunctionHooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) nebo [SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) .  
  
 `FunctionIDMapper2`Metodu lze nastavit pouze jednou. doporučujeme ji nastavit ve zpětném volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [SetFunctionIDMapper –](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
