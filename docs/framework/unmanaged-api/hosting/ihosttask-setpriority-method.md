---
title: IHostTask::SetPriority – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6888e11038af09e797ebaff5a97107ceb8d662e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority – metoda
Požadavky, že hostitel upravit prioritu podprocesu úrovně pro úlohu reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `newPriority`  
 [v] Celé číslo, které představuje hodnota priority požadovaný přístup z více vláken pro úlohu reprezentována aktuální `IHostTask` instance.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetPriority` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Vlákna jsou uděleno zpracování přihlášení pomocí kruhového dotazování systém, který je částečně založená na úroveň priority vlákno. `SetPriority` Umožňuje CLR nastavit úroveň priority tento přístup z více vláken pro aktuální úlohu. Následující `newPriority` hodnoty jsou podporovány.  
  
-   THREAD_PRIORITY_ABOVE_NORMAL  
  
-   THREAD_PRIORITY_BELOW_NORMAL  
  
-   THREAD_PRIORITY_HIGHEST  
  
-   THREAD_PRIORITY_IDLE  
  
-   THREAD_PRIORITY_LOWEST  
  
-   THREAD_PRIORITY_NORMAL  
  
-   THREAD_PRIORITY_TIME_CRITICAL  
  
 Volání CLR `SetPriority` při hodnotu <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> se mění pomocí uživatelského kódu. Hostitel můžete definovat vlastní algoritmy pro přístup z více vláken s prioritou přiřazení a může tuto žádost ignorovat.  
  
> [!NOTE]
>  `SetPriority` nevytváří sestavu zda byl změněn úroveň priority přístup z více vláken. Volání [ihosttask::getpriority –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) k určení hodnoty úroveň priority úkolu přístup z více vláken.  
  
 Přístup z více vláken s prioritou úrovně hodnoty jsou definovány Win32 `SetThreadPriority` funkce. Další informace o priorita vlákna naleznete v dokumentaci k platformě Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [GetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
