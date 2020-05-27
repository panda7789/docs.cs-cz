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
ms.openlocfilehash: f8f476f681764a46700dd5ec83c8f9b2739f18f6
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842488"
---
# <a name="ihosttask-interface"></a>IHostTask – rozhraní
Poskytuje metody, které umožňují, aby modul CLR (Common Language Runtime) komunikoval s hostitelem a spravoval úlohy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alert – metoda](ihosttask-alert-method.md)|Požaduje, aby hostitel probudil úlohu reprezentovanou aktuální `IHostTask` instancí, aby bylo možné úlohu přerušit.|  
|[GetPriority – metoda](ihosttask-getpriority-method.md)|Získá úroveň priority vlákna úkolu reprezentované aktuální `IHostTask` instancí.|  
|[Join – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Zablokuje volající úlohu, dokud není dokončena úloha reprezentovaná aktuální `IHostTask` instancí, zadaný časový interval vypršel nebo je volána metoda [IHostTask:: Alert](ihosttask-alert-method.md) .|  
|[SetCLRTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Přidruží instanci [rozhraní ICLRTask](iclrtask-interface.md) k aktuální `IHostTask` instanci.|  
|[SetPriority – metoda](ihosttask-setpriority-method.md)|Požaduje, aby hostitel upravil úroveň priority vlákna pro úlohu reprezentovanou aktuální `IHostTask` instancí.|  
|[Start – metoda](ihosttask-start-method.md)|Požaduje, aby hostitel přesunul úlohu představovanou aktuální `IHostTask` instancí z pozastaveného stavu do aktivního stavu, ve kterém lze spustit kód.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metody definované `IHostTask` pro spuštění úlohy, nastavení úrovně priority vlákna a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
