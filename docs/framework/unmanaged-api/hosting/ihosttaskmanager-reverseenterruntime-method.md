---
title: "IHostTaskManager::ReverseEnterRuntime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.ReverseEnterRuntime
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69743f6b7229f89d19d4134a11bb5f37fe5ca928
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a>IHostTaskManager::ReverseEnterRuntime – metoda
Upozorní hostitele, že se provádí volání do common language runtime (CLR) z nespravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`ReverseEnterRuntime`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti je k dispozici k dokončení přidělení požadovaný prostředek.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud ve spravovaném kódu je provedeno volání do modulu CLR z pořadí, které pochází, každé volání `ReverseEnterRuntime` odpovídá volání [reverseleaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md).  
  
> [!NOTE]
>  Volání můžete bez vnořenými pocházejí z nespravovaného kódu. V takovém případě není bez volání [enterruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [leaveruntime –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), nebo `ReverseLeaveRuntime`a počet volání `ReverseEnterRuntime` se nerovná počtu volání `ReverseLeaveRuntime`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
