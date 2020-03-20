---
title: ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176991"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
Poskytuje rámec zásobníku funkce, která je hlášena profiler funkcí [FunctionTailcall3WithInfo.](functiontailcall3withinfo-function.md) Tuto metodu lze volat `FunctionTailcall3WithInfo` pouze během zpětného volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [v] Funkce, `FunctionID` která se vrací.  
  
 `eltInfo`  
 [v] Neprůhledný popisovač, který představuje informace o daném rámci zásobníku. Profiler by měl `eltInfo` poskytnout stejné, které bylo `FunctionTailcall3WithInfo` dáno profiler funkce.  
  
 `pFrameInfo`  
 [out] Neprůhledný popisovač, který představuje obecné informace o daném rámci zásobníku. Tento popisovač je `FunctionTailcall3WithInfo` platný pouze během zpětného `GetFunctionTailcall3Info` volání, ve kterém profiler volal metodu.  
  
## <a name="remarks"></a>Poznámky  
  
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
