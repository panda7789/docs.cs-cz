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
ms.openlocfilehash: 55411f187e2ef73997633d94b37a7d5d2cfd74c9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868561"
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
 pro `FunctionID` funkce, která se zadává.  
  
 `eltInfo`  
 pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku. Profiler by měl poskytnout stejnou `eltInfo`, že byl dán funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku. Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětného volání, ve kterém Profiler volal metodu `GetFunctionEnter3Info`.  
  
 `pcbArgumentInfo`  
 [in, out] Ukazatel na celkovou velikost [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury (včetně všech dalších [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktur pro rozsahy argumentů, na které odkazuje `pArgumentInfo`). Pokud zadaná velikost není dostatečná, je vrácena ERROR_INSUFFICIENT_BUFFER a očekávaná velikost je uložena v `pcbArgumentInfo`. Chcete-li volat `GetFunctionEnter3Info` pouze k načtení očekávané hodnoty pro `*pcbArgumentInfo`, nastavte `*pcbArgumentInfo`= 0 a `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 mimo Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) strukturu, která popisuje umístění argumentů funkce v paměti v pořadí zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Profiler musí přidělit dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu kontrolované funkce a musí určit velikost v parametru `pcbArgumentInfo`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
