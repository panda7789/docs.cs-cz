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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aef7866d912951972ec9c66efccca671c3787da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a>IHostSyncManager::SetCLRSyncManager – metoda
Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální [ihostsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pManager`  
 [v] Ukazatel na `ICLRSyncManager` instance poskytl common language runtime (CLR).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetCLRSyncManager` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Usnadňuje komunikaci mezi hostitelem a modulu CLR rozhraní hostování obecně pocházet v párech. Jeden člen, které odpovídá páru je implementováno modulem hostitele a jiné člen je implementováno modulem modulu CLR. Jako na straně hostitele implementace `IHostSyncManager` rozhraní odpovídá `ICLRSyncManager` rozhraní implementované modulu CLR. Volání CLR `SetCLRSyncManager` k poskytování `ICLRSyncManager` instance pro hostitele, který chcete přidružit k aktuální `IHostSyncManager` instance.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
