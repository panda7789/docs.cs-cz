---
title: IHostTaskManager::CallNeedsHostHook – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 5bc5752d4d2b772b1d18f438c4daaa1b8938da9e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842345"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook – metoda
Umožňuje hostiteli určit, zda může modul CLR (Common Language Runtime) vložit zadané volání do nespravované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `target`  
 pro Adresa v mapovaném souboru přenositelného spustitelného souboru (PE) nespravované funkce, která má být volána.  
  
 `pbCallNeedsHostHook`  
 mimo Ukazatel na logickou hodnotu, která označuje, zda hostitel vyžaduje, aby volání bylo zavěšeno.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé závažnosti selhání. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Pro usnadnění optimalizace provádění kódu provede modul CLR analýzu volání vyvolání každé platformy během kompilace, aby bylo možné určit, zda lze volání vložit do řádku. `CallNeedsHostHook`umožňuje hostiteli přepsat toto rozhodnutí tím, že vyžaduje, aby se zavolalo volání nespravované funkce. Pokud hostitel vyžaduje zavěšení, modul runtime nevloží volání.  
  
 Hostitel obvykle vyžaduje zavěšení, kde musí upravit stav s plovoucí desetinnou čárkou, nebo po přijetí oznámení, že volání zadává stav, kde hostitel nemůže sledovat požadavky na paměť v modulu runtime nebo jakékoli zámky. Pokud hostitel vyžaduje, aby bylo volání zavěšeno, modul runtime upozorní hostitele přechodů do a ze spravovaného kódu pomocí volání [EnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)a [ReverseLeaveRuntime –](ihosttaskmanager-reverseleaveruntime-method.md).  
  
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
