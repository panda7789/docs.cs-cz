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
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496591"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info – metoda
Poskytuje informace o snímku zásobníku a argumentu funkce, která je hlášena v profileru funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) . Tuto metodu lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro `FunctionID`Funkce, která se zadává.  
  
 `eltInfo`  
 pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Profiler by měl poskytnout stejný, jako by `eltInfo` byl dán funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku. Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětného volání, ve kterém Profiler volal `GetFunctionEnter3Info` metodu.  
  
 `pcbArgumentInfo`  
 [in, out] Ukazatel na celkovou velikost [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury (včetně všech dalších [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktur pro rozsahy argumentů, na které ukazuje `pArgumentInfo` ). Pokud zadaná velikost není dostatečná, je vrácena ERROR_INSUFFICIENT_BUFFER a očekávaná velikost je uložena v `pcbArgumentInfo` . Chcete-li volat `GetFunctionEnter3Info` pouze pro načtení očekávané hodnoty pro `*pcbArgumentInfo` , nastavte `*pcbArgumentInfo` = 0 a `pArgumentInfo` = null.  
  
 `pArgumentInfo`  
 mimo Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) strukturu, která popisuje umístění argumentů funkce v paměti v pořadí zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Profiler musí přidělit dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu kontrolované funkce a musí indikovat velikost v `pcbArgumentInfo` parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
