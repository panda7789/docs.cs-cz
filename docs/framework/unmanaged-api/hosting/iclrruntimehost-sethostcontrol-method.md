---
title: "ICLRRuntimeHost::SetHostControl – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.SetHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9727144e9504a5a3ad7ae2529286440d07633b2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl – metoda
Nastaví ukazatele rozhraní, modul CLR (CLR) můžete získat implementace hostitele [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHostControl`  
 [v] Ukazatele rozhraní k implementaci hostitele [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetHostControl`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Modul CLR již byl inicializován.|  
  
## <a name="remarks"></a>Poznámky  
 Je třeba volat `SetHostControl` před modulu CLR inicializací, který je před voláním [metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) nebo použít některou z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Doporučuje se, že zavoláte `SetHostControl` ihned po volání [corbindtocurrentruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) nebo [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
