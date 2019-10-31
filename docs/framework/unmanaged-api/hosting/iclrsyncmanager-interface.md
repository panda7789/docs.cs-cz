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
ms.openlocfilehash: 3593e4d68058a1820f575c92ff9571d43560316a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133923"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager – rozhraní
Definuje metody, které umožní hostiteli získat informace o požadovaných úlohách a zjišťovat zablokování v jeho implementaci synchronizace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator – metoda](iclrsyncmanager-createrwlockowneriterator-method.md)|Požadavky, které modul CLR (Common Language Runtime) vytvoří iterátor, který může hostitel použít k určení sady úloh čekajících na zámek pro zápis čtenářů.|  
|[DeleteRWLockOwnerIterator – metoda](iclrsyncmanager-deleterwlockowneriterator-method.md)|Požaduje, aby modul CLR zničil iterátor, který byl vytvořen voláním `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner – metoda](iclrsyncmanager-getmonitorowner-method.md)|Získá úkol, který vlastní zadané monitorování.|  
|[GetRWLockOwnerNext – metoda](iclrsyncmanager-getrwlockownernext-method.md)|Získá další úkol, který čeká na aktuální zámek zapisovače pro čtení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread>
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- [Spravované a nespravované zřetězení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [Rozhraní pro hostování](hosting-interfaces.md)
