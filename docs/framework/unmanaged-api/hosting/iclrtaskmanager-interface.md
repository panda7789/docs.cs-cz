---
title: "ICLRTaskManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 342d7b82802fcfbe9e179d85d6d692205f19e382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
