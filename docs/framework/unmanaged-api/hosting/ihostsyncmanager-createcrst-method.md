---
title: "IHostSyncManager::CreateCrst – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f932c91892292c787feecf1768c33fb429334bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a>IHostSyncManager::CreateCrst – metoda
Vytvoří objekt kritická sekce modulu pro synchronizaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCrst`  
 [out] Ukazatel na adresu [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instanci implementované pro hostitele, nebo hodnotu null, pokud nebylo možné vytvořit kritická sekce.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateCrst`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebylo k dispozici pro její vytvoření požadovaný kritické.|  
  
## <a name="remarks"></a>Poznámky  
 Kritická sekce objekty poskytují synchronizace podobná poskytované objekt mutex, s tím rozdílem, že kritické oddíly mohou být používány pouze vláken v jednom procesu. `CreateCrst`odpovídá Win32 `InitializeCriticalSection` funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostCrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [Mutex – třídy](../../../../docs/standard/threading/mutexes.md)  
 [Semaphore a SemaphoreSlim](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
