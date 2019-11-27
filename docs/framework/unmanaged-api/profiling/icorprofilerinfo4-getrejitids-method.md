---
title: ICorProfilerInfo4::GetReJITIDs – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: f6d26abba649b608858fde8beaac750600493869
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442864"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs – metoda
Vrátí pole ID, které identifikují všechny verze rekompilovaných kompilátorů JIT zadané funkce, které jsou stále přiděleny. To zahrnuje verze rekompilovaných funkcí JIT, které byly následně obnoveny, ale nebyly dosud uvolněny (například pokud je stále používána doména aplikace obsahující vrácená funkce).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 pro `FunctionID` instance funkce, pro kterou chcete vytvořit výčet verzí.  
  
 `cReJitIds`  
 pro Počet ID rekompilovaných rekompilovaných JIT přidělených v poli `reJitIds`.  
  
 `pcReJitIds`  
 mimo Skutečný počet rekompilovaných ID JIT.  
  
 `reJitIds`  
 mimo Pole přidělené volajícím, které bude obsahovat ID rekompilovaných JIT pro danou funkci.  
  
## <a name="remarks"></a>Poznámky  
 `GetReJITIDs` vytvoří výčet aktivních rekompilovaných ID JIT pro danou instanci funkce. Řídí se stejným vzorem použití jako s jinými `ICorProfilerInfo` funkcemi, které přijímají vyrovnávací paměti přidělené volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
