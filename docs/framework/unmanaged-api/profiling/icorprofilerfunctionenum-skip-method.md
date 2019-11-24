---
title: ICorProfilerFunctionEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: d2a0bff0d3d93ab8542699cffd3d0ecc032246ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448208"
---
# <a name="icorprofilerfunctionenumskip-method"></a>ICorProfilerFunctionEnum::Skip – metoda
Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] The number of elements to be skipped.  
  
## <a name="return-value"></a>Návratová hodnota  
 This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`celt` elements were skipped.|  
|S_FALSE|Fewer than `celt` elements were skipped, which indicates that there are no more elements.|  
  
## <a name="remarks"></a>Poznámky  
 The new position of this enumerator's cursor is (current position) + `celt`.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerFunctionEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
