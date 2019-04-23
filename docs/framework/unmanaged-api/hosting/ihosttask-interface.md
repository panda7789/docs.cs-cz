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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb15da31d91565d49df83099045f742866eebcaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081499"
---
# <a name="ihosttask-interface"></a>IHostTask – rozhraní
Poskytuje metody, které umožňují common language runtime (CLR) ke komunikaci s hostitelem ke správě úloh.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Alert – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Požadavky, že hostitel probuzení úloh reprezentovaný aktuální `IHostTask` instance, tak můžete přeruší úlohu.|  
|[GetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Získá úroveň priority vlákna úloh reprezentovaný aktuální `IHostTask` instance.|  
|[Join – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blokuje volající úlohou, dokud není úloha reprezentované aktuální `IHostTask` instance dokončení, o zadaný časový interval uplyne, nebo [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) je volána.|  
|[SetCLRTask – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Přidruží [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s aktuálním `IHostTask` instance.|  
|[SetPriority – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Požadavky, že hostitel upravit priorita vlákna na úrovni úkolů reprezentované aktuální `IHostTask` instance.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Požadavky, že hostitel move – úloha reprezentované aktuální `IHostTask` instanci z režimu spánku za provozu stavu, ve kterém lze kód spustit.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metody definované `IHostTask` spuštění úlohy, nastavit její prioritu vlákna úroveň, a tak dále.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
