---
title: ICLRGCManager::GetStats – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504222"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats – metoda
Získá sadu aktuálních statistik o systému uvolňování paměti modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStats`  
 [in, out] Instance [COR_GC_STATS](cor-gc-stats-structure.md) , která obsahuje požadované statistiky.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`GetStats`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 CLR vypočítá a vrátí pouze ty statistiky, které jsou určeny `Flags` polem `pStats` .  
  
 Nastavte `Flags` pole na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , aby se určilo, které statistiky ve [COR_GC_STATS](cor-gc-stats-structure.md) struktuře mají být nastavené.  
  
 Příklad použití je následující:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS – struktura](cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES – výčet](cor-gc-stat-types-enumeration.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICLRGCManager – rozhraní](iclrgcmanager-interface.md)
- [Rozhraní hostování CLR](clr-hosting-interfaces.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
