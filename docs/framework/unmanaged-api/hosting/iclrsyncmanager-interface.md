---
title: ICLRSyncManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e4affa363083ce55ac3764c26412a0d60ba3f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203090"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager – rozhraní
Definuje metody, které umožňují hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator – metoda](iclrsyncmanager-createrwlockowneriterator-method.md)|Požadavky, které modul CLR (CLR) vytvořit iterátor pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.|  
|[DeleteRWLockOwnerIterator – metoda](iclrsyncmanager-deleterwlockowneriterator-method.md)|Požadavky, že modul CLR zničit iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner – metoda](iclrsyncmanager-getmonitorowner-method.md)|Získá úkol, který vlastní zadané monitorování.|  
|[GetRWLockOwnerNext – metoda](iclrsyncmanager-getrwlockownernext-method.md)|Získá další úkol, který čeká na uzamčení čtení a zápis.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Spravovaná a nespravovaná vlákna](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Rozhraní pro hostování](hosting-interfaces.md)
