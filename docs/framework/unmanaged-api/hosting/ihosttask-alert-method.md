---
title: IHostTask::Alert – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 057e2aafff726b187f36b8b52859b2f2e812e70e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskalert-method"></a>IHostTask::Alert – metoda
Požadavky, že hostitel wake úlohu reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, takže úlohu můžete byl zrušen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Volání CLR `Alert` metoda při <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> je volána z uživatelského kódu, nebo když <xref:System.AppDomain> přidružené k aktuální <xref:System.Threading.Thread> ukončí. Hostitel musí vracet okamžitě, protože při volání asynchronně. Pokud hostitel nemůže výstrahy úloha okamžitě, musí probuzení při příštím přejde do stavu, ve kterém můžete generovat výstrahy.  
  
> [!NOTE]
>  `Alert` ovlivňuje pouze ty úlohy, do kterých byla úspěšná modulu runtime [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnotu WAIT_ALERTABLE metody, jako [připojení](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
