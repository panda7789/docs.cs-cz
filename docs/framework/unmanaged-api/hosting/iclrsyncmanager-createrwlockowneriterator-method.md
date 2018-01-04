---
title: "ICLRSyncManager::CreateRWLockOwnerIterator – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.CreateRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f74a15bb58f0ee62b56204e2b145ae64ff7dd59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator – metoda
Požadavky, které modul CLR (CLR) vytvořit iterace pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cookie`  
 [v] Soubor cookie přidružený zámek požadované čtení a zápis.  
  
 `pIterator`  
 [out] Ukazatel na iterátor, který se dá předat do [getrwlockownernext –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) a [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`byla volána na vlákno, které běží v současné době spravovaného kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitelé obvykle volání `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, a `GetRWLockOwnerNext` metod zjišťování zablokování. Hostitel je odpovědný za dodržování, čtení a zápis zámek je stále platný, protože modulu CLR nesnaží se zámek čtení a zápis zachování připojení. Několik strategií jsou k dispozici pro hostitele zajistit platnost zámku:  
  
-   Hostitel může blokovat verzi volání na čtení a zápis zámek (například [ihostsemaphore::releasesemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) a zajistit, že tento blok nezpůsobí vzájemného zablokování.  
  
-   Hostitel může blokovat ukončení z čekání na objekt události související s zámek čtení a zápis znovu zajistíte, že tento blok nezpůsobí vzájemného zablokování.  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator`musí být volána pouze na vláken, které aktuálně provádějí nespravovaného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
