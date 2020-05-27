---
title: IHostSecurityManager::GetSecurityContext – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: e43eb7ebfc367e7d4a7a209a5037fcc4566cd7ec
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803931"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a>IHostSecurityManager::GetSecurityContext – metoda
Získá požadovaná [IHostSecurityContext –](ihostsecuritycontext-interface.md) z hostitele.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `eContextType`  
 pro Jedna z hodnot [EContextType –](econtexttype-enumeration.md) , která označuje typ kontextu zabezpečení, který se má vrátit.  
  
 `ppSecurityContext`  
 mimo Adresa ukazatele rozhraní na `IHostSecurityContext` `eContextType` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetSecurityContext`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může řídit veškerý přístup kódu k tokenům vláken jak CLR, tak i uživatelský kód. Může také zajistit, aby byly kompletní informace o kontextu zabezpečení předány přes asynchronní operace nebo body kódu s omezeným přístupem ke kódu. `IHostSecurityContext`Zapouzdřuje tyto informace kontextu zabezpečení, které jsou neprůhledné pro CLR. Modul CLR tyto informace zachytí a přesune je napříč fondem vláken pracovní položky, provádění finalizační metody a konstrukce modulu a třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EContextType – výčet](econtexttype-enumeration.md)
- [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)
- [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)
