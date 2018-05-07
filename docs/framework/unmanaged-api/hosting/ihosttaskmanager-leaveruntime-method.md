---
title: IHostTaskManager::LeaveRuntime – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime – metoda
Upozorní hostitele, aktuálně prováděné úlohy je nechte common language runtime (CLR) a zadejte nespravovaného kódu.  
  
> [!IMPORTANT]
>  Odpovídající volání [ihosttaskmanager::enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorní hostitele aktuálně prováděné úlohy je nutnosti opětovného zadávání spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `target`  
 [v] Adresa v rámci namapované přenosné spustitelný soubor nespravované funkce, která se má volat.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Je k dispozici k dokončení požadované přidělení není dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Mohou být vnořené pořadí volání do a z nespravovaného kódu. Například následující seznam popisuje hypotetický situace, ve kterém je pořadí volání `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), a `IHostTaskManager::EnterRuntime` umožňuje hostitele k identifikaci vnořené vrstvy.  
  
|Akce|Odpovídající volání metody|  
|------------|-------------------------------|  
|Vyvolání nespravované funkce napsané v jazyce C pomocí platformy spravované spustitelné volání jazyka Visual Basic.|`IHostTaskManager::LeaveRuntime`|  
|Nespravované funkce C volá metodu v spravovanou knihovnu DLL napsané v C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Spravované funkce jazyka C# volá jinou funkci nespravované napsané v jazyce C, také pomocí platformy vyvolání.|`IHostTaskManager::LeaveRuntime`|  
|Nespravované funkce second vrátí provádění funkce jazyka C#.|`IHostTaskManager::EnterRuntime`|  
|Funkce jazyka C# vrací provádění první nespravované funkce.|`IHostTaskManager::ReverseLeaveRuntime`|  
|První nespravované funkce vrátí provádění programu jazyka Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
