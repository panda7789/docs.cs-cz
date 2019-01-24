---
title: ICLRSyncManager::CreateRWLockOwnerIterator – metoda
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3554d351512f48aad65872dd9ae82d084552d518
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600242"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator – metoda
Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cookie`  
 [in] Soubor cookie, přidružené k požadované čtení a zápis zámku.  
  
 `pIterator`  
 [out] Ukazatel na iterátor, který lze předat [getrwlockownernext –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) a [deleterwlockowneriterator –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) metody.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator` byla volána pro vlákno, které aktuálně běží spravovaný kód.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitelé obvykle volání `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, a `GetRWLockOwnerNext` metod rozpoznávání zablokování. Hostitel zodpovídá za to, že zámek pro čtení a zápis je stále platný, protože modul CLR nesnaží se zachování zámku pro čtení a zápis. Jsou dostupné pro hostitele, aby platnost zámku několik strategií:  
  
-   Hostitel zablokovat volání uvolnění zámku pro čtení a zápis (například [ihostsemaphore::releasesemaphore –](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) při zajištění, že tento blok způsobit zablokování.  
  
-   Hostitel může blokovat výstupu z čekání na událost objekt přidružený k zámku pro čtení a zápis, znovu zajistit, že tento blok způsobit zablokování.  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator` musí být volána pouze na vlákna, která jsou aktuálně spuštěny nespravovaného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
