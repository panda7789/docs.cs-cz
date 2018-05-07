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
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager – rozhraní
Definuje metody, které umožňují hostitele k načtení informací o požadovaných úkolů a ke zjištění zablokování v jeho implementaci synchronizace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator – metoda](iclrsyncmanager-createrwlockowneriterator-method.md)|Požadavky, které modul CLR (CLR) vytvořit iterace pro hostitele použít k určení sady úloh čeká na zámek čtení a zápis.|  
|[DeleteRWLockOwnerIterator – metoda](iclrsyncmanager-deleterwlockowneriterator-method.md)|Požadavky, že modulu CLR destroy iterátor, který byl vytvořen volání `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner – metoda](iclrsyncmanager-getmonitorowner-method.md)|Získá úloha, která vlastní zadaný monitorování.|  
|[GetRWLockOwnerNext – metoda](iclrsyncmanager-getrwlockownernext-method.md)|Získá další úloha, která čeká na aktuální zámek čtení a zápis.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread>  
 [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)  
 [Spravovaná a nespravovaná vlákna](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [Rozhraní pro hostování](hosting-interfaces.md)
