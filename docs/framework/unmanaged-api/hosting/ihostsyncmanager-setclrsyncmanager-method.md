---
title: IHostSyncManager::SetCLRSyncManager – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 7f1832b22a1b80855f48eba6d39bff64da6fa5f9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501440"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a>IHostSyncManager::SetCLRSyncManager – metoda
Nastaví instanci [ICLRSyncManager](iclrsyncmanager-interface.md) k přidružení k aktuální instanci [IHostSyncManager](ihostsyncmanager-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pManager`  
 pro Ukazatel na `ICLRSyncManager` instanci poskytnutou modulem CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetCLRSyncManager`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Aby bylo možné zjednodušit komunikaci mezi hostitelem a modulem CLR, jsou rozhraní hostování obecně uvedena ve dvojicích. Jeden člen dvojice je implementován hostitelem a druhý člen je implementován modulem CLR. Jako implementace na straně hostitele `IHostSyncManager` odpovídá rozhraní `ICLRSyncManager` rozhraní implementovanému modulem CLR. Modul CLR volá `SetCLRSyncManager` zadání `ICLRSyncManager` instance pro hostitele, který má být přidružen k aktuální `IHostSyncManager` instanci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
