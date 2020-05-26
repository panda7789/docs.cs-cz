---
title: IHostCrst::SetSpinCount – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804873"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount – metoda
Nastaví počet číselníků pro aktuální instanci [IHostCrst](ihostcrst-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwSpinCount`  
 pro Nový počet číselníků pro aktuální `IHostCrst` instanci.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetSpinCount`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 U systémů s více procesory platí, že pokud je kritická část reprezentovaná aktuální `IHostCrst` instancí nedostupná, volající vlákno se `dwSpinCount` před voláním [IHostSemaphore:: vyčká](ihostsemaphore-wait-method.md) na semaforu přidruženého k důležité části. Pokud se kritická část uvolní během operace otáčení, volající vlákno se vyhne operaci čekání.  
  
 Použití `dwSpinCount` je stejné jako použití parametru se stejným názvem ve `InitializeCriticalSectionAndSpinCount` funkci Win32.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostCrst – rozhraní](ihostcrst-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
