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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855939"
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
 pro `FunctionID` Instance funkce, pro kterou chcete vytvořit výčet verzí.  
  
 `cReJitIds`  
 pro Počet ID rekompilovaných rekompilovaných JIT přidělených `reJitIds` v poli  
  
 `pcReJitIds`  
 mimo Skutečný počet rekompilovaných ID JIT.  
  
 `reJitIds`  
 mimo Pole přidělené volajícím, které bude obsahovat ID rekompilovaných JIT pro danou funkci.  
  
## <a name="remarks"></a>Poznámky  
 `GetReJITIDs`Vytvoří výčet aktivních rekompilovaných ID JIT pro danou instanci funkce. Řídí se stejným vzorem použití jako jiné `ICorProfilerInfo` funkce, které přijímají vyrovnávací paměti přidělené volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
