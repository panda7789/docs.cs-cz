---
title: "IHostControl::SetAppDomainManager – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.SetAppDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d689a664f5bad19a70a8d635beb1f25f33da6ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager – metoda
Upozorní hostitele vytvořený domény aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppDomainID`  
 [v] Číselný identifikátor vybrané <xref:System.AppDomain>.  
  
 `pUnkAppDomainManager`  
 [v] Ukazatel <xref:System.AppDomainManager> objekt, který implementuje hostitele jako `IUnknown`.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetAppDomainManager`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.AppDomainManager> Hostitel poskytuje mechanismus k navázání připojení do spravovaného kódu a k řízení vytvoření a nastavení jednotlivých <xref:System.AppDomain>. <xref:System.AppDomainManager> Je načten do každé <xref:System.AppDomain> při který <xref:System.AppDomain> je vytvořena. Pokud se rozhodne, modulu CLR upozorní hostitele domény aplikace vytvořila nastavením hodnoty `pUnkAppDomainManager` parametr.  
  
 Při implementaci `SetAppDomainManager` metody hostitele můžete nastavit název sestavení a typ pro správce domény aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
