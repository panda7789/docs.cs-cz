---
title: IHostGCManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: 6f7158bcac7ad22647104e2041da959285d2be8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130483"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager – rozhraní
Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementovaného modulem CLR (Common Language Runtime).  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[SuspensionEnding – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|Upozorňuje hostitele, že modul CLR pokračuje v provádění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.|  
|[SuspensionStarting – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|Upozorní hostitele, že modul CLR pozastaví provádění úloh a provede uvolňování paměti.|  
|[ThreadIsBlockingForSuspension – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
