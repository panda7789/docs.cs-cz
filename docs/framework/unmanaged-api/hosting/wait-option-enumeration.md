---
title: WAIT_OPTION – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ac28f28d4d284ba26fadd46e53ebeb8e5b5f3cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139578"
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION – výčet
Obsahuje hodnoty, které označují, že by akce hostitele zabrat Pokud operace požadoval společné bloky language runtime (CLR).  
  
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
|`WAIT_ALERTABLE`|Upozorňuje hostitele, že úloha se probudí, modul CLR volá-li [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.|  
|`WAIT_MSGPUMP`|Upozorňuje hostitele, že ho musí pump zprávy v aktuálním vlákně operačního systému, pokud vlákno bude blokováno. Modul runtime určuje pouze na tuto hodnotu <xref:System.Threading.ApartmentState.STA> vlákna.|  
|`WAIT_NOTINDEADLOCK`|Upozorňuje hostitele, nelze rozdělit žádost o synchronizaci zadaný hostitel. To znamená, nejde vrátit hostitele `HOST_E_DEADLOCK`.|  
  
## <a name="remarks"></a>Poznámky  
 [Ihosttaskmanager::Sleep –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) a [ihosttaskmanager::switchtotask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody obou přijímají parametr tohoto typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
