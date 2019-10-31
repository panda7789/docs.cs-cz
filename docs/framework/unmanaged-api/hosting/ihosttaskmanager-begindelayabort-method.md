---
title: IHostTaskManager::BeginDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: b765d5449cebbdec5f106a8e4743fee2f0ee5521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133137"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a>IHostTaskManager::BeginDelayAbort – metoda
Upozorňuje hostitele, že spravovaný kód vstupuje do období, ve kterém musí být aktuální úloha přerušena.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`BeginDelayAbort` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_UNEXPECTED|`BeginDelayAbort` už je zavolaná, ale odpovídající volání [EndDelayAbort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) ještě není přijaté.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel nesmí přerušit aktuální úlohu, dokud není volána `EndDelayAbort`. Pokud je provedeno jiné volání `BeginDelayAbort` bez navázání volání `EndDelayAbort`, hostitel by měl vrátit E_UNEXPECTED z `BeginDelayAbort`a neměla by mít žádnou akci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
