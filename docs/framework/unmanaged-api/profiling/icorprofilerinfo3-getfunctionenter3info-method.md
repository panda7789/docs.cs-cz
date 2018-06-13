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
ms.openlocfilehash: e5d06988330b9ec83463165661ea5425d8563c60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459052"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info – metoda
Poskytuje informace zásobníku rámec a argument funkce, která je hlášena profileru pomocí [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce. Tuto metodu lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] `FunctionID` Funkce, který jste právě zadali.  
  
 `eltInfo`  
 [v] Neprůhledného popisovače, který představuje informace o daném zásobníku. Profileru by měl poskytovat stejné `eltInfo` se určí podle [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce.  
  
 `pFrameInfo`  
 [out] Neprůhledného popisovače, který představuje obecné informace o daném zásobníku. Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětného volání, ve kterém se nazývá profileru `GetFunctionEnter3Info` metoda.  
  
 `pcbArgumentInfo`  
 [ve out] Ukazatel na celkovou velikost v bajtech z [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturu (a všechny další [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury pro argument rozsahy, na kterou odkazuje`pArgumentInfo`). Pokud po zadanou velikost není dost, je vrácen ERROR_INSUFFICIENT_BUFFER a očekávané velikosti je uložen v `pcbArgumentInfo`. K volání `GetFunctionEnter3Info` jenom k načtení očekávaná hodnota pro `*pcbArgumentInfo`, nastavte `*pcbArgumentInfo`= 0 a `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která popisuje umístění argumenty v paměti, v pořadí zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Profileru přidělíte dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktura funkce, která je ke kontrole a musí označovat velikost v `pcbArgumentInfo` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [Functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
