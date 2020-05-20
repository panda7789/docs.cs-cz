---
title: EMemoryAvailable – výčet
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 822396e28d000a5309738680fec502e1aeacd67c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616213"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable – výčet
Obsahuje hodnoty, které udávají množství volné fyzické paměti v počítači. Tyto hodnoty logicky mapují na události pro vysokou a nízkou paměť vrácenou `CreateMemoryResourceNotification` funkcí v rozhraní API systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|K dispozici je dostatek fyzické paměti.|  
|`eMemoryAvailableLow`|K dispozici je jen málo fyzické paměti.|  
|`eMemoryAvailableNeutral`|Dostupná fyzická paměť je neutrální.|  
  
## <a name="remarks"></a>Poznámky  
 Tato hodnota je předána hostitelem do modulu CLR (Common Language Runtime) pomocí volání metody [ICLRMemoryNotificationCallback –:: OnMemoryNotification –](iclrmemorynotificationcallback-onmemorynotification-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
