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
ms.openlocfilehash: 2939f13933c4681e7e2220e5290e019e10c2844e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841916"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime – metoda
Upozorňuje hostitele, že aktuálně vykonávaný úkol se chystá opustit modul CLR (Common Language Runtime) a zadat nespravovaný kód.  
  
> [!IMPORTANT]
> Odpovídající volání [IHostTaskManager:: EnterRuntime –](ihosttaskmanager-enterruntime-method.md) upozorní hostitele, že aktuálně prováděná úloha předává spravovaný kód.  
  
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
 Sekvence volání do a z nespravovaného kódu mohou být vnořeny. Například následující seznam popisuje hypotetickou situaci, ve které sekvence volání `LeaveRuntime` , [IHostTaskManager:: ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime –](ihosttaskmanager-reverseleaveruntime-method.md)a `IHostTaskManager::EnterRuntime` umožňuje hostiteli identifikovat vnořené vrstvy.  
  
|Akce|Odpovídající volání metody|  
|------------|-------------------------------|  
|Spravovaný spustitelný soubor Visual Basic volá nespravovanou funkci napsanou v jazyce C pomocí vyvolání platformy.|`IHostTaskManager::LeaveRuntime`|  
|Nespravovaná funkce jazyka C volá metodu ve spravované knihovně DLL napsané v jazyce C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Spravovaná funkce jazyka C# volá jinou nespravovanou funkci napsanou v jazyce C a zároveň používá vyvolání platformy.|`IHostTaskManager::LeaveRuntime`|  
|Druhá nespravovaná funkce vrátí provedení do funkce jazyka C#.|`IHostTaskManager::EnterRuntime`|  
|Funkce jazyka C# vrátí provedení první nespravované funkci.|`IHostTaskManager::ReverseLeaveRuntime`|  
|První nespravovaná funkce vrátí provedení Visual Basic programu.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
