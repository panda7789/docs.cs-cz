---
title: IHostSyncManager::CreateCrstWithSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 86bc320c28a5fbf122d234a4a1f15b674628c0b5
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803400"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a>IHostSyncManager::CreateCrstWithSpinCount – metoda
Vytvoří objekt kritického oddílu s počtem číselníků pro synchronizaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwSpinCount`  
 pro Určuje počet číselníků pro objekt kritické sekce.  
  
 `ppCrst`  
 mimo Ukazatel na adresu instance [IHostCrst](ihostcrst-interface.md) nebo hodnotu null, pokud nelze vytvořit oddíl Critical.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pro vytvoření požadovaného kritického oddílu není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počet číselníků se používá jenom v systému s více procesory. Počet číselník určuje počet pokusů, které volající vlákno musí provést před tím, než provede operaci čekání na semaforu, který je přidružen k nedostupnému kritickému oddílu. Pokud se kritická část uvolní během operace otáčení, volající vlákno se vyhne operaci čekání. `CreateCrstWithSpinCount`zrcadlí `InitializeCriticalSectionAndSpinCount` funkci Win32.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSemaphore – rozhraní](ihostsemaphore-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
