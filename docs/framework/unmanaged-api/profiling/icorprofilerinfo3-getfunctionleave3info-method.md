---
title: ICorProfilerInfo3::GetFunctionLeave3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: bacb50520df9f1553226ec6bf1e878238b64bb17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449706"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info – metoda
Poskytuje rámec zásobníku a návratovou hodnotu funkce, která je hlášena profileru funkcí [FunctionLeave3WithInfo – Function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) . Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro `FunctionID` funkce, která vrací.  
  
 `eltInfo`  
 pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Profiler by měl poskytnout stejnou `eltInfo`, která byla přidělena profileru funkcí [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) .  
  
 `pFrameInfo`  
 mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku. Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětného volání, ve kterém Profiler volal metodu `GetFunctionLeave3Info`.  
  
 `pRetvalRange`  
 mimo Ukazatel na strukturu [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) , která obsahuje hodnotu vrácenou z funkce. Chcete-li získat přístup k informacím o vrácených hodnotách, musí být nastaven příznak `COR_PRF_ENABLE_FUNCTION_RETVAL`. Profiler může použít [metodu ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) k nastavení příznaků událostí.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
