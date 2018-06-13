---
title: ICLRPolicyManager::SetActionOnTimeout – metoda
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc1d16a2d57fea27c1c26fc55fbbfa9b74c25495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435835"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a>ICLRPolicyManager::SetActionOnTimeout – metoda
Určuje akci zásady, které modul CLR (CLR) má provést, pokud zadaná operace vyprší časový limit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `operation`  
 [v] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) hodnoty, která určuje operaci, pro který chcete zadat časový limit akce. Podporovány jsou následující hodnoty:  
  
-   OPR_AppDomainUnload  
  
-   OPR_ProcessExit  
  
-   OPR_ThreadRudeAbortInCriticalRegion  
  
-   OPR_ThreadRudeAbortInNonCriticalRegion  
  
 `action`  
 [v] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, který udává akci zásady mají být provedeny, když vyprší časový limit operace.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetActionOnTimeout` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Nelze nastavit vypršení časového limitu pro zadaný `operation`, nebo byla zadána neplatná hodnota pro `operation`.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota časového limitu může být buď výchozí časový limit stanovené CLR, nebo má hodnotu pro hostitele v volání [iclrpolicymanager::setTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) metoda.  
  
 Ne všechny akce hodnoty zásad lze zadat jako chování vypršení časového limitu pro operace CLR. `SetActionOnTimeout` Obvykle se používá pouze pro zvýšení chování. Například hostitel můžete určit, že vlákno přerušení být převedena na článku neslušní vláken přerušení, ale nelze zadat jako opak. Následující tabulka popisuje platném `action` hodnoty platný `operation` hodnoty.  
  
|Hodnota pro `operation`|Platné hodnoty pro `action`|  
|---------------------------|-------------------------------|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|-eRudeAbortThread<br />-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_AppDomainUnload|-eUnloadAppDomain<br />-eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
|OPR_ProcessExit|-eExitProcess<br />-eFastExitProcess<br />-eRudeExitProcess<br />-eDisableRuntime|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrOperation – výčet](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
