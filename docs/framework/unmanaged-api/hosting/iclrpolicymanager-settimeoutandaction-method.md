---
title: "ICLRPolicyManager::SetTimeoutAndAction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeoutAndAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67150b7544f1d8d25532c564800404b634cae99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a>ICLRPolicyManager::SetTimeoutAndAction – metoda
Nastaví hodnotu časového limitu pro zadanou operaci a určuje zásad akci, kterou common language runtime (CLR) má provést, když dojde k operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `operation`  
 [v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje operaci, pro kterou chcete nastavit časový limit a zásady `action`. Podporovány jsou následující hodnoty:  
  
-   OPR_AppDomainUnload  
  
-   OPR_ProcessExit  
  
-   OPR_ThreadRudeAbortInCriticalRegion  
  
-   OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `dwMilliseconds`  
 [v] Nová hodnota časového limitu, v milisekundách. Hodnota NEKONEČNÉ příčiny `operation` nikdy k vypršení časového limitu.  
  
 `action`  
 [v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci zásady, kterou modulu CLR by měla provést v případě `operation` dojde.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetTimeoutAndAction`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `action`.|  
  
## <a name="remarks"></a>Poznámky  
 `SetTimeoutAndAction`zapouzdřuje funkce [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) a [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody a může být volána místo sekvenční volání na tyto dvě metody.  
  
> [!IMPORTANT]
>  Ne všechny akce hodnoty zásad lze zadat jako chování vypršení časového limitu pro operace CLR. Najdete v částech poznámky témat pro tyto dvě metody platné hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [SetActionOnTimeout – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)  
 [Iclrpolicymanager::settimeoutandaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
