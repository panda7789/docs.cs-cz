---
title: ICorProfilerModuleEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type:
- apiref
ms.openlocfilehash: 7a3ad94a4149d6ebb70e077926771e28d7f82779
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494810"
---
# <a name="icorprofilermoduleenumnext-method"></a>ICorProfilerModuleEnum::Next – metoda
Získá zadaný počet souvislých modulů ze sekvenční kolekce modulů počínaje aktuální pozicí čítače výčtu v sekvenci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet modulů, které se mají načíst.  
  
 `ids`  
 mimo Pole `ModuleID` hodnot, z nichž každý představuje načtený modul.  
  
 `pceltFetched`  
 mimo Ukazatel na počet prvků skutečně vrácených v `ids` poli.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`celt`prvky byly vráceny.|  
|S_FALSE|`celt`Bylo vráceno méně než prvků, což indikuje, že byl výčet dokončen.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerModuleEnum – rozhraní](icorprofilermoduleenum-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
