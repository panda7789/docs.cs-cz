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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73098077e3860d3f4a8a02921ecedf8dff24165b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774058"
---
# <a name="etasktype-enumeration"></a>ETaskType – výčet
Obsahuje hodnoty, které označují typ úlohy, která je reprezentována buď [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) nebo [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) rozhraní.  
  
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
  
|Člen|Popis|  
|------------|-----------------|  
|`TT_ADUNLOAD`|Rozhraní představuje úlohu uvolňování domény aplikace.|  
|`TT_DEBUGGERHELPER`|Rozhraní představuje pomocné rutiny úkol ladicího programu.|  
|`TT_FINALIZER`|Rozhraní představuje úlohu finalizační metodu.|  
|`TT_GC`|Rozhraní představuje úlohu uvolňování paměti kolekce.|  
|`TT_THREADPOOL_GATE`|Rozhraní představuje úlohu vlákno brány.|  
|`TT_THREADPOOL_IOCOMPLETION`|Rozhraní představuje úlohu vláken vstupně-výstupních operací nebo úkol vlákno port dokončení.|  
|`TT_THREADPOOL_TIMER`|Rozhraní představuje úlohu časovače vláken.|  
|`TT_THREADPOOL_WAIT`|Rozhraní představuje vlákno úkol čekání.|  
|`TT_THREADPOOL_WORKER`|Rozhraní představuje úlohy vlákna pracovního procesu.|  
|`TT_UNKNOWN`|Úloha neznámý.|  
|`TT_USER`|Rozhraní představuje uživatelského úkolu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
