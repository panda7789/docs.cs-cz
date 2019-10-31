---
title: IHostTask – rozhraní
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121397"
---
# <a name="ihosttask-interface"></a>IHostTask – rozhraní
Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) komunikoval s hostitelem a spravoval úlohy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alert – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Vyžádá, aby hostitel probudil úlohu reprezentovanou aktuální instancí `IHostTask`, takže úkol může být přerušen.|  
|[GetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Získá úroveň priority vlákna úlohy reprezentované aktuální instancí `IHostTask`.|  
|[Join – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Zablokuje volající úlohu, dokud se nedokončí úkol, který je reprezentován aktuální `IHostTask` instance, zadaného časového intervalu vypršela nebo [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.|  
|[SetCLRTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Přidruží instanci [rozhraní ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) k aktuální instanci `IHostTask`.|  
|[SetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální instancí `IHostTask`.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Požaduje, aby hostitel přesunul úlohu představovanou aktuální `IHostTask` instance z pozastaveného stavu do aktivního stavu, ve kterém lze kód spustit.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metody definované `IHostTask` pro spuštění úlohy, nastavení úrovně priority vlákna a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
