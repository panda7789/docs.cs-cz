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
ms.openlocfilehash: 4c57a3fde3565a21800c60794b6c2d1c7616ddd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007998"
---
# <a name="wait_option-enumeration"></a>WAIT_OPTION – výčet
Obsahuje hodnoty, které určují akci, kterou by měl hostitel provést, pokud je operace požadována v rámci bloků modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|Upozorní hostitele, že by měl být úkol probuzeny, pokud CLR volá metodu [IHostTask:: Alert](ihosttask-alert-method.md) .|  
|`WAIT_MSGPUMP`|Upozorní hostitele, že musí pumpovat zprávy v aktuálním vláknu operačního systému, pokud se vlákno zablokuje. Modul runtime tuto hodnotu určuje pouze v <xref:System.Threading.ApartmentState.STA> vlákně.|  
|`WAIT_NOTINDEADLOCK`|Upozorní hostitele, že zadaný požadavek na synchronizaci nemůže být hostitelem. To znamená, že hostitel nemůže vracet `HOST_E_DEADLOCK` .|  
  
## <a name="remarks"></a>Poznámky  
 Metody [IHostTaskManager:: Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) a [IHostTaskManager:: SwitchToTask –](ihosttaskmanager-switchtotask-method.md) obě přebírají parametr tohoto typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
