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
ms.openlocfilehash: 81da8052b79047933b4afc6d5686029465d83eba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191494"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime – metoda
Upozorňuje hostitele, že právě prováděnou úlohu se chystá nechte common language runtime (CLR) a zadejte nespravovaného kódu.  
  
> [!IMPORTANT]
>  Odpovídající volání [ihosttaskmanager::enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorňuje hostitele, že je právě prováděnou úlohu pokuste spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 [in] Adresa v mapovaných přenosný spustitelný soubor nespravovanou funkci, která se má volat.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti je k dispozici k dokončení požadované přidělení.|  
  
## <a name="remarks"></a>Poznámky  
 Mohou být vnořené sekvence volání do a z nespravovaného kódu. Například následující seznam popisuje hypotetické situace, ve kterém pořadí volání `LeaveRuntime`, [ihosttaskmanager::reverseenterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [ihosttaskmanager::reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), a `IHostTaskManager::EnterRuntime` umožňuje tak hostitele kvůli identifikaci vnořených vrstev.  
  
|Akce|Odpovídající volání metody|  
|------------|-------------------------------|  
|Spravované spustitelný soubor volá jazyka Visual Basic vyvolat nespravovanou funkci napsané v jazyce C s použitím platformy.|`IHostTaskManager::LeaveRuntime`|  
|Nespravovaná funkce C volá metodu v spravovaná knihovna DLL, napsaný v C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Spravovanou C# funkce volá jinou nespravované funkci napsané v jazyce C, také pomocí platformy vyvolat.|`IHostTaskManager::LeaveRuntime`|  
|Druhá nespravované funkce vrátí provádění C# funkce.|`IHostTaskManager::EnterRuntime`|  
|C# Funkce vrátí vykonávání do první nespravované funkci.|`IHostTaskManager::ReverseLeaveRuntime`|  
|První nespravované funkce vrátí vykonávání do programu Visual Basic.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
