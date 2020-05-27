---
title: IHostSyncManager::CreateRWLockWriterEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803150"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a>IHostSyncManager::CreateRWLockWriterEvent – metoda
Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 pro Soubor cookie, který se má přidružit k události automatického resetování.  
  
 `ppEvent`  
 mimo Ukazatel na adresu instance [IHostAutoEvent](ihostautoevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockWriterEvent`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá `CreateRWLockWriterEvent` metodu, aby získal odkaz na `IHostAutoEvent` instanci, která se má použít při implementaci zámku zapisovače. Hostitel může pomocí zadaného souboru cookie určit, které úlohy čekají na zámek voláním metod iterace rozhraní [ICLRSyncManager](iclrsyncmanager-interface.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](ihostautoevent-interface.md)
- [IHostManualEvent – rozhraní](ihostmanualevent-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
