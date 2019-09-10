---
title: ICLRSyncManager::GetRWLockOwnerNext – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetRWLockOwnerNext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2461d20dc65706fcfdb8b9a2088d634c771fa1fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855587"
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a>ICLRSyncManager::GetRWLockOwnerNext – metoda
Získá další instanci [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , která je blokována aktuálním zámkem zapisovače čtenář.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Iterator`  
 pro Iterátor, který byl vytvořen pomocí volání [CreateRWLockOwnerIterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).  
  
 `ppOwnerHostTask`  
 mimo Ukazatel na další `IHostTask` , který čeká na zámek, nebo hodnotu null, pokud úloha nečeká.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetRWLockOwnerNext`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ppOwnerHostTask` je nastaven na hodnotu null, iterace se ukončí a hostitel by měl volat metodu [DeleteRWLockOwnerIterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) .  
  
> [!NOTE]
> Rozhraní CLR volá `AddRef` na, `IHostTask` které `ppOwnerHostTask` odkazuje na to, aby se zabránilo ukončení této úlohy, zatímco hostitel obsahuje ukazatel. Hostitel musí volat, `Release` aby po dokončení vyvolal počet odkazů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
