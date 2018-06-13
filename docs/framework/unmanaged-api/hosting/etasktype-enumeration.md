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
ms.openlocfilehash: c8609857f142000245aef4326c8ef7490e6d4c95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430593"
---
# <a name="etasktype-enumeration"></a>ETaskType – výčet
Obsahuje hodnoty, které označují typ úlohy, která je reprezentována buď [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) nebo [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`TT_ADUNLOAD`|Rozhraní představuje úkol uvolnění domény aplikace aplikace.|  
|`TT_DEBUGGERHELPER`|Rozhraní představuje úlohu pomocná ladicí program.|  
|`TT_FINALIZER`|Rozhraní představuje úlohu finalizační metodu.|  
|`TT_GC`|Rozhraní představuje kolekci úlohu uvolňování paměti.|  
|`TT_THREADPOOL_GATE`|Rozhraní představuje úlohu brány přístup z více vláken.|  
|`TT_THREADPOOL_IOCOMPLETION`|Rozhraní představuje vstupně-výstupních operací vlákno úlohy nebo úlohu dokončení port přístup z více vláken.|  
|`TT_THREADPOOL_TIMER`|Rozhraní představuje úlohu časovače vláken.|  
|`TT_THREADPOOL_WAIT`|Rozhraní představuje úlohu čekání přístup z více vláken.|  
|`TT_THREADPOOL_WORKER`|Rozhraní představuje úlohu pracovní vlákno.|  
|`TT_UNKNOWN`|Tato úloha neznámý.|  
|`TT_USER`|Rozhraní představuje úlohu uživatele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
