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
ms.openlocfilehash: a801afeac690c02ef08652a923c31be14967cdc0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465788"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask – metoda
Požádá o explicitně, že modul CLR (CLR) vytvoří nový úkol.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTask`  
 [out] Ukazatel na adresu nově vytvořeného [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), nebo hodnota null, pokud úlohu nelze vytvořit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda vrátila úspěšně.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti je možné přidělit požadovaný prostředek.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR vytvoří nový úkol automaticky při inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v <xref:System.Threading> obor názvů, nebo když je vyšší velikost fondu vláken. Také vytvoří úkoly při nespravovaný kód zavolá spravované funkce.  
  
 `CreateTask` umožňuje hostiteli, aby požadavek na explicitní, CLR vytvoří nový úkol. Například můžete hostitele vyvolat tuto metodu za účelem předem inicializovat datové struktury.  
  
> [!IMPORTANT]
>  Nová úloha se vrátí v pozastaveném stavu a činnost průvodce zůstává přerušena dokud explicitně volá hostitele [ihosttask::Start –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
