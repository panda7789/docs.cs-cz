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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177017"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info – metoda
Poskytuje zásobníku rámce a argument informace o funkci, která je hlášena profiler funkce [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkce. Tuto metodu lze volat `FunctionEnter3WithInfo` pouze během zpětného volání.  
  
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
 [v] Funkce, `FunctionID` která je zadána.  
  
 `eltInfo`  
 [v] Neprůhledný popisovač, který představuje informace o daném rámci zásobníku. Profiler by měl `eltInfo` poskytnout stejné, které bylo dáno [functionEnter3WithInfo](functionenter3withinfo-function.md) funkce.  
  
 `pFrameInfo`  
 [out] Neprůhledný popisovač, který představuje obecné informace o daném rámci zásobníku. Tento popisovač je `FunctionEnter3WithInfo` platný pouze během zpětného `GetFunctionEnter3Info` volání, ve kterém profiler volal metodu.  
  
 `pcbArgumentInfo`  
 [dovnitř, ven] Ukazatel na celkovou velikost [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury v bajtech (plus všechny další [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktury pro `pArgumentInfo`rozsahy argumentů, na které odkazuje ). Pokud zadaná velikost nestačí, ERROR_INSUFFICIENT_BUFFER je vrácena `pcbArgumentInfo`a očekávaná velikost je uložena v . Chcete-li `GetFunctionEnter3Info` volat pouze pro `*pcbArgumentInfo`načtení očekávané hodnoty pro , nastavte `*pcbArgumentInfo`=0 a `pArgumentInfo`=NULL.  
  
 `pArgumentInfo`  
 [out] Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury, která popisuje umístění argumentů funkce v paměti, v pořadí zleva doprava.  
  
## <a name="remarks"></a>Poznámky  
 Profiler musí přidělit dostatek `COR_PRF_FUNCTION_ARGUMENT_INFO` místa pro strukturu funkce, která je kontrolována `pcbArgumentInfo` a musí uvádět velikost v parametru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [FunkceEnter3WithInfo](functionenter3withinfo-function.md)
- [FunkceLeave3WithInfo](functionleave3withinfo-function.md)
- [FunkceTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilování](index.md)
