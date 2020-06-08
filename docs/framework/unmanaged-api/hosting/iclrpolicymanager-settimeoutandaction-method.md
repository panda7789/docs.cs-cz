---
title: ICLRPolicyManager::SetTimeoutAndAction – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 02e836601be72d54f561e077cd3c466470bafb25
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504092"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction – metoda
Nastaví hodnotu časového limitu pro zadanou operaci a určuje akci zásad, kterou by modul CLR (Common Language Runtime) měl provést při výskytu operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `operation`  
 pro Jedna z hodnot [EClrOperation –](eclroperation-enumeration.md) s informacemi o operaci, pro kterou chcete nastavit časový limit a zásadu `action` . Podporovány jsou následující hodnoty:  
  
- OPR_AppDomainUnload  
  
- OPR_ProcessExit  
  
- OPR_ThreadRudeAbortInCriticalRegion  
  
- OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 pro Nová hodnota časového limitu v milisekundách. Hodnota nekonečna má `operation` nikdy neomezený časový limit.  
  
 `action`  
 pro Jedna z hodnot [EPolicyAction –](epolicyaction-enumeration.md) , která označuje akci zásad, při které by měl modul CLR provést `operation` .  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Pro zadanou hodnotu nelze nastavit časový limit `operation` nebo byla zadána neplatná hodnota pro `action` .|  
  
## <a name="remarks"></a>Poznámky  
 `SetTimeoutAndAction`Zapouzdřuje možnosti metod [ICLRPolicyManager:: setTimeout](iclrpolicymanager-settimeout-method.md) a [ICLRPolicyManager:: SetActionOnTimeout –](iclrpolicymanager-setactionontimeout-method.md) a lze je volat místo sekvenčních volání těchto dvou metod.  
  
> [!IMPORTANT]
> Ne všechny hodnoty akcí zásad lze zadat jako časový limit pro operace CLR. Platné hodnoty najdete v částech poznámky v tématech pro tyto dvě metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrOperation – výčet](eclroperation-enumeration.md)
- [EPolicyAction – výčet](epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [SetActionOnTimeout – metoda](iclrpolicymanager-setactionontimeout-method.md)
- [ICLRPolicyManager:: Settimeoutandaction –](iclrpolicymanager-settimeoutandaction-method.md)
