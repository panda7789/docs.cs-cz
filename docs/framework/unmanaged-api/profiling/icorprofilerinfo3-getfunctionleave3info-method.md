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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d51462017287d42fd468ed0a74a2e83203a3d94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000620"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info – metoda
Poskytuje rámec zásobníku a návratovou hodnotu funkce, která se hlásí do profileru pomocí [functionleave3withinfo – funkce](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce. Tuto metodu lze volat pouze během `FunctionLeave3WithInfo` zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Funkce, která vrací.  
  
 `eltInfo`  
 [in] Neprůhledný popisovač, který představuje informace o daném zásobníku. Profiler by měl poskytovat stejné `eltInfo` , který byl zadán do profileru pomocí [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkce.  
  
 `pFrameInfo`  
 [out] Neprůhledný popisovač, který představuje obecné informace o daném zásobníku. Tento popisovač je platný pouze během `FunctionLeave3WithInfo` zpětné volání, ve kterém profiler volal `GetFunctionLeave3Info` metoda.  
  
 `pRetvalRange`  
 [out] Ukazatel [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturu, která obsahuje hodnotu, která je vrácena z funkce. Přístup k informacím návratová hodnota `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak. Profiler může použít [ICorProfilerInfo::SetEventMask – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) nastavit příznaky událostí.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
