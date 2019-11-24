---
title: ICorProfilerThreadEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: aaa8eaa2c4eb927a817425611f71e51c9f3d37af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447576"
---
# <a name="icorprofilerthreadenumskip-method"></a>ICorProfilerThreadEnum::Skip – metoda
Advances the enumerator's cursor from its current position to skip the specified number of elements.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
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
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerThreadEnum – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
