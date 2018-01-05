---
title: "ICLRControl::GetCLRManager – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.GetCLRManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 197a3818de8d0b17331a9f9ac422ecaabb230a50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager – metoda
Získá ukazatele rozhraní k instanci jakýkoli z typů správce, které hostitele můžete použít ke konfiguraci common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [v] `IID` Typu manager vrátit. Následující `IID` hodnoty jsou podporovány.  
  
-   IID_ICLRDebugManager: Určuje, že `ppObject` bude typu [iclrdebugmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).  
  
-   IID_ICLRErrorReportingManager: Určuje, že `ppObject` bude typu [iclrerrorreportingmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).  
  
-   IID_ICLRGCManager: Určuje, že `ppObject` bude typu [iclrgcmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
-   IID_ICLRHostProtectionManager: Určuje, že `ppObject` bude typu [iclrhostprotectionmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).  
  
-   IID_ICLROnEventManager: Určuje, že `ppObject` bude typu [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).  
  
-   IID_ICLRPolicyManager: Určuje, že `ppObject` bude typu [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).  
  
-   IID_ICLRTaskManager: speciries, `ppObject` bude typu [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).  
  
 `ppObject`  
 [out] Ukazatel rozhraní požadovaný manager, nebo hodnotu null, pokud byl požadován typ neplatného správce.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|Typ rozhraní není podporován.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
