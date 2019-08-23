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
ms.openlocfilehash: 8b2e8e636915b3921fcd727fc78a3fb18fc69104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959039"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime – metoda
Upozorňuje hostitele, že aktuálně vykonávaný úkol se chystá opustit modul CLR (Common Language Runtime) a zadat nespravovaný kód.  
  
> [!IMPORTANT]
> Odpovídající volání [IHostTaskManager:: EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) upozorní hostitele, že aktuálně prováděná úloha předává spravovaný kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 pro Adresa v mapovaném přenositelném spustitelném souboru nespravované funkce, která má být volána.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K dokončení požadovaného přidělení není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Sekvence volání do a z nespravovaného kódu mohou být vnořeny. Například následující seznam `LeaveRuntime`popisuje hypotetickou situaci, ve které sekvence volání, [IHostTaskManager:: ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)a `IHostTaskManager::EnterRuntime` umožňuje hostiteli Identifikujte vnořené vrstvy.  
  
|Akce|Odpovídající volání metody|  
|------------|-------------------------------|  
|Spravovaný spustitelný soubor Visual Basic volá nespravovanou funkci napsanou v jazyce C pomocí vyvolání platformy.|`IHostTaskManager::LeaveRuntime`|  
|Nespravovaná funkce jazyka C volá metodu ve spravované knihovně DLL napsané v C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Spravovaná C# funkce volá jinou nespravovanou funkci napsanou v jazyce C, používá také vyvolání platformy.|`IHostTaskManager::LeaveRuntime`|  
|Druhá nespravovaná funkce vrátí provedení do C# funkce.|`IHostTaskManager::EnterRuntime`|  
|C# Funkce vrátí provedení první nespravované funkci.|`IHostTaskManager::ReverseLeaveRuntime`|  
|První nespravovaná funkce vrátí provedení Visual Basic programu.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
