---
title: ICorProfilerInfo3::GetFunctionEnter3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164824"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info – metoda
Poskytuje informace zásobníku rámce a argumentů funkce, která se hlásí do profileru pomocí [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce. Tuto metodu lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Funkce, která je právě zadán.  
  
 `eltInfo`  
 [in] Neprůhledný popisovač, který představuje informace o daném zásobníku. Profiler by měl poskytovat stejné `eltInfo` , který byl zadán ve [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce.  
  
 `pFrameInfo`  
 [out] Neprůhledný popisovač, který představuje obecné informace o daném zásobníku. Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětné volání, ve kterém profiler volal `GetFunctionEnter3Info` metoda.  
  
 `pcbArgumentInfo`  
 [out v] Ukazatel na celkovou velikost v bajtech, z [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturu (a všechny další [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur pro argument rozsahy, na které odkazuje `pArgumentInfo`). Pokud zadané velikosti není dostatek, je vrácena ERROR_INSUFFICIENT_BUFFER a očekávaná velikost je uložena v `pcbArgumentInfo`. Pro volání `GetFunctionEnter3Info` jenom k načtení očekávanou hodnotou pro `*pcbArgumentInfo`, nastavte `*pcbArgumentInfo`= 0 a `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která popisuje umístění argumenty v paměti, v pořadí zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Profiler musí přidělit dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkce, která je kontrolován a musíte uvést velikost v `pcbArgumentInfo` parametru.  
  
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
