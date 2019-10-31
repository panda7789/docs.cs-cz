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
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092191"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager – rozhraní
Poskytuje metody, které umožňují hostiteli explicitně požádat, aby modul CLR (Common Language Runtime) vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil geografickou jazyk a jazykovou verzi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Požadavky explicitně, aby CLR vytvořil novou instanci [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) .|  
|[GetCurrentTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Získá instanci `ICLRTask`, která představuje aktuálně prováděnou úlohu.|  
|[GetCurrentTaskType – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Získá typ úlohy, která je právě prováděna.|  
|[SetLocale – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Upozorní CLR, že hostitel změnil identifikátor národního prostředí v aktuálně spuštěné úloze.|  
|[SetUILocale – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Upozorní modul CLR (Common Language Runtime), že hostitel změnil identifikátor národního prostředí uživatelského rozhraní v aktuálně spuštěné úloze.|  
  
## <a name="remarks"></a>Poznámky  
 Každý úkol, který běží v hostovaném prostředí, má znázornění na straně hostitele (instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Hostitel nebo modul CLR může iniciovat vytvoření úlohy, ale reprezentace na straně hostitele musí být přidružena k odpovídajícímu vyjádření na straně CLR, aby bylo zajištěno úspěšné propojení mezi hostitelem a modulem CLR týkajícím se úlohy. Aby bylo možné spustit spravovaný kód ve vlákně operačního systému, je třeba vytvořit tyto dva objekty a vytvořit jejich instanci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
