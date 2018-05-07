---
title: ICLRTaskManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14c2c9b70ac2e57983ea4b16772add6a1dff5ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager – rozhraní
Poskytuje metody, které umožňují na hostiteli a požadavku explicitně, modul CLR (CLR) vytvořit nový úkol, získat aktuálně spuštěné úlohy a nastavit zeměpisné language a jazykovou verzi pro úlohu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Výslovně požaduje, aby vytvořil novou modulu CLR [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.|  
|[GetCurrentTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Získá `ICLRTask` instanci, která představuje úloha, která je aktuálně spuštěné.|  
|[GetCurrentTaskType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Získá typ úlohy, který je aktuálně spuštěné.|  
|[SetLocale – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Upozorní modulu CLR, že hostitel změnil identifikátor národního prostředí na aktuálně spuštěné úlohy.|  
|[SetUILocale – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Upozorní modul common language runtime, že hostitel změnil identifikátor národního prostředí uživatelského rozhraní na aktuálně spuštěné úlohy.|  
  
## <a name="remarks"></a>Poznámky  
 Každý úkol, který běží v hostovaném prostředí má reprezentace i na straně hostitele (instance [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Hostitele nebo modulu CLR může spustit vytvoření úlohy, avšak reprezentace straně hostitele musí být přidružen znázornění odpovídající CLR straně zajistit úspěšné komunikaci mezi hostitelem a CLR týkající se úloha. Tyto dva objekty musí být vytvořen a vytvořit její instanci před spravovaný kód můžete spustit na vláknu operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
