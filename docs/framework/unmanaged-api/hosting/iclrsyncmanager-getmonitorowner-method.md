---
title: ICLRSyncManager::GetMonitorOwner – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: 77debe047f5b379237022f44ef8f9d96718b227d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762497"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner – metoda
Získá instanci [IHostTask](ihosttask-interface.md) , která vlastní monitor identifikovaný zadaným souborem cookie.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 pro Soubor cookie přidružený k monitoru  
  
 `ppOwnerHostTask`  
 mimo Ukazatel na `IHostTask` , který aktuálně vlastní monitor, nebo hodnotu null, pokud nemá žádná úloha vlastnictví.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel obvykle volá `GetMonitorOwner` jako součást mechanismu zjišťování vzájemného zablokování. Soubor cookie je přidružen k monitoru, když je vytvořen pomocí volání metody [IHostSyncManager:: CreateMonitorEvent –](ihostsyncmanager-createmonitorevent-method.md).  
  
> [!NOTE]
> Volání pro vydanou událost, která je podkladem, může monitor blokovat – ale nebude zablokovat – Pokud je volání této metody aktuálně platné pro soubor cookie přidružený k tomuto monitoru. Jiné úlohy mohou také zablokovat, pokud se pokusí získat toto monitorování.  
  
 `GetMonitorOwner`vždy vrátí hodnotu okamžitě a lze ji volat kdykoli po volání `CreateMonitorEvent` . Hostitel nemusí čekat, dokud úloha nečeká na událost.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
