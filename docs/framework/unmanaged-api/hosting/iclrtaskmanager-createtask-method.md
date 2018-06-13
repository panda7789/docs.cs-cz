---
title: ICLRTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f731e121324793a027c5977a02e1973b0d6fff20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439645"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask – metoda
Explicitně požadavků, že modul CLR (CLR) vytvořit novou úlohu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTask`  
 [out] Ukazatel na adresu nově vytvořený [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), nebo hodnota null, pokud úlohy se nezdařilo.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Je k dispozici přidělit požadovaný prostředek není dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR vytvoří novou úlohu automaticky při inicializaci, když uživatelský kód vytvoří vlákno pomocí typy v <xref:System.Threading> obor názvů, nebo když se zvýší velikost fondu vláken. Vytváří také úlohy, když nespravovaný kód zavolá spravované funkce.  
  
 `CreateTask` umožňuje hostiteli, aby požadavek explicitní, modul CLR vytvořit novou úlohu. Například můžete hostitele vyvolat tuto metodu za účelem preinitialize datové struktury.  
  
> [!IMPORTANT]
>  Nová úloha je vrácený v pozastaveném stavu a zůstává přerušena, dokud hostitel explicitně volá [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
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
