---
title: ETaskType – výčet
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 0fa72568df77c4916a3c6676e1dcca7c0c616c4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493315"
---
# <a name="etasktype-enumeration"></a>ETaskType – výčet
Obsahuje hodnoty, které určují typ úlohy, který je reprezentován buď [ICLRTask](iclrtask-interface.md) nebo rozhraním [IHostTask](ihosttask-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`TT_ADUNLOAD`|Rozhraní představuje úlohu uvolnění domény aplikace.|  
|`TT_DEBUGGERHELPER`|Rozhraní představuje úlohu pomocníka ladicího programu.|  
|`TT_FINALIZER`|Rozhraní představuje úlohu finalizační metody.|  
|`TT_GC`|Rozhraní představuje úlohu uvolňování paměti.|  
|`TT_THREADPOOL_GATE`|Rozhraní představuje úlohu vlákna brány.|  
|`TT_THREADPOOL_IOCOMPLETION`|Rozhraní představuje úlohu vstupně-výstupního vlákna nebo úlohu vlákna portu pro dokončení.|  
|`TT_THREADPOOL_TIMER`|Rozhraní představuje úlohu vlákna časovače.|  
|`TT_THREADPOOL_WAIT`|Rozhraní představuje úlohu vlákna čekání.|  
|`TT_THREADPOOL_WORKER`|Rozhraní představuje úlohu pracovního vlákna.|  
|`TT_UNKNOWN`|Úloha je neznámá.|  
|`TT_USER`|Rozhraní představuje úkol uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty hostování](hosting-enumerations.md)
