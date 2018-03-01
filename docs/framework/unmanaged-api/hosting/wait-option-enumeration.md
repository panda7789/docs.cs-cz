---
title: "WAIT_OPTION – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 143c191592efe8cfea8049f0dd5dc05a5bd4192f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION – výčet
Obsahuje hodnoty, které označují, že akce hostitele by měl trvat, pokud operace požadoval běžné bloky runtime (CLR) jazyk.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Hostitele upozorní, že úloha se probudí, modul CLR volá-li [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metoda.|  
|`WAIT_MSGPUMP`|Zprávy v aktuální vlákno operačního systému se musí čerpadla, když se stane zablokuje vlákno upozorní hostitele. Modul runtime určuje jenom na tuto hodnotu <xref:System.Threading.ApartmentState.STA> přístup z více vláken.|  
|`WAIT_NOTINDEADLOCK`|Upozorní hostitele, že žádost o synchronizaci zadaný nelze rozdělit hostitele. To znamená, nemůže vrátit hostitele `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Poznámky  
 [Ihosttaskmanager::Sleep –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) a [ihosttaskmanager::switchtotask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody obou přijímají parametr tohoto typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
