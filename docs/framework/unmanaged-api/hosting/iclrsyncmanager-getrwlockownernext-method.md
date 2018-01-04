---
title: "ICLRSyncManager::GetRWLockOwnerNext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetRWLockOwnerNext
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetRWLockOwnerNext
helpviewer_keywords:
- ICLRSyncManager::GetRWLockOwnerNext method [.NET Framework hosting]
- GetRWLockOwnerNext method [.NET Framework hosting]
ms.assetid: 0e025b6a-280e-40a2-a2d0-b15f58777b81
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1181cbb71aa30281fbff634354162e1f245d05fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagergetrwlockownernext-method"></a>ICLRSyncManager::GetRWLockOwnerNext – metoda
Získá další [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, který je blokovaný na aktuální zámek čtení a zápis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRWLockOwnerNext (  
    [in] SIZE_T       Iterator,  
    [out] IHostTask  *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Iterator`  
 [v] Iterator, který byl vytvořen pomocí volání [createrwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).  
  
 `ppOwnerHostTask`  
 [out] Ukazatel na další `IHostTask` , čeká na zámek, nebo hodnota null, pokud žádná úloha čeká.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetRWLockOwnerNext`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `ppOwnerHostTask` je nastaven na hodnotu null, ukončilo iterace a měla by volat hostitele [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metoda.  
  
> [!NOTE]
>  Volání CLR `AddRef` na `IHostTask` ke kterému `ppOwnerHostTask` body zabránit tato úloha ukončení při hostitele obsahuje ukazatele. Hostitel musí volat `Release` se sníží počet odkazů až po dokončení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
