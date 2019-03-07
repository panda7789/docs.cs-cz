---
title: IHostControl::SetAppDomainManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83461f89be9a16305da2732536dcc6847b45027d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482558"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager – metoda
Upozorňuje hostitele, vytvoření domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainID`  
 [in] Číselný identifikátor vybraného <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [in] Ukazatel <xref:System.AppDomainManager> objekt, který implementuje hostitele jako `IUnknown`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.AppDomainManager> Hostitel poskytuje mechanismus ke spuštění do spravovaného kódu a řídit vytváření a nastavení jednotlivých <xref:System.AppDomain>. <xref:System.AppDomainManager> Je načteno do každé <xref:System.AppDomain> při, který <xref:System.AppDomain> se vytvoří. Pokud se zvolí, modul CLR upozorňuje hostitele, že doména aplikace se vytvořila tak, že nastavíte hodnotu `pUnkAppDomainManager` parametru.  
  
 V jeho provádění `SetAppDomainManager` metody hostitele můžete nastavit název sestavení a typ pro správce domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
