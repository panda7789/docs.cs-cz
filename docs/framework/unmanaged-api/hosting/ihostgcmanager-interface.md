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
ms.openlocfilehash: 428e4cf8997713b08e40d9376c34ae5eee8cfa32
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804858"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager – rozhraní
Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementovaného modulem CLR (Common Language Runtime).  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[SuspensionEnding – metoda](ihostgcmanager-suspensionending-method.md)|Upozorňuje hostitele, že modul CLR pokračuje v provádění úloh na vláknech, které byly pozastaveny pro uvolňování paměti.|  
|[SuspensionStarting – metoda](ihostgcmanager-suspensionstarting-method.md)|Upozorní hostitele, že modul CLR pozastaví provádění úloh a provede uvolňování paměti.|  
|[ThreadIsBlockingForSuspension – metoda](ihostgcmanager-threadisblockingforsuspension-method.md)|Upozorní hostitele, že vlákno, ze kterého bylo volání metody provedeno, bude zablokovat pro uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
