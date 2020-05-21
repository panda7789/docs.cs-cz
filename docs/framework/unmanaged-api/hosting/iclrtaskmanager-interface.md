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
ms.openlocfilehash: 9e26071181e8e0712c753fa03d5e16eb85e5ee68
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762824"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager – rozhraní
Poskytuje metody, které umožňují hostiteli explicitně požádat, aby modul CLR (Common Language Runtime) vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil geografickou jazyk a jazykovou verzi.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateTask – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Požadavky explicitně, aby CLR vytvořil novou instanci [ICLRTask](iclrtask-interface.md) .|  
|[GetCurrentTask – metoda](iclrtaskmanager-getcurrenttask-method.md)|Načte `ICLRTask` instanci, která představuje aktuálně prováděnou úlohu.|  
|[GetCurrentTaskType – metoda](iclrtaskmanager-getcurrenttasktype-method.md)|Získá typ úlohy, která je právě prováděna.|  
|[SetLocale – metoda](iclrtaskmanager-setlocale-method.md)|Upozorní CLR, že hostitel změnil identifikátor národního prostředí v aktuálně spuštěné úloze.|  
|[SetUILocale – metoda](iclrtaskmanager-setuilocale-method.md)|Upozorní modul CLR (Common Language Runtime), že hostitel změnil identifikátor národního prostředí uživatelského rozhraní v aktuálně spuštěné úloze.|  
  
## <a name="remarks"></a>Poznámky  
 Každý úkol, který běží v hostovaném prostředí, má znázornění na straně hostitele (instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) a na straně CLR (instance [ICLRTask](iclrtask-interface.md)). Hostitel nebo modul CLR může iniciovat vytvoření úlohy, ale reprezentace na straně hostitele musí být přidružena k odpovídajícímu vyjádření na straně CLR, aby bylo zajištěno úspěšné propojení mezi hostitelem a modulem CLR týkajícím se úlohy. Aby bylo možné spustit spravovaný kód ve vlákně operačního systému, je třeba vytvořit tyto dva objekty a vytvořit jejich instanci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
