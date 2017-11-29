---
title: "EMemoryAvailable – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable – výčet
Obsahuje hodnoty, které označují množství volného fyzické paměti v počítači. Tyto hodnoty logicky mapování na události pro maximální a minimální paměti vrácená z `CreateMemoryResourceNotification` funkce v rozhraní API Win32.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Množství fyzické paměti je k dispozici.|  
|`eMemoryAvailableLow`|Velmi malé fyzické paměti je k dispozici.|  
|`eMemoryAvailableNeutral`|Dostupná fyzická paměť je neutrální.|  
  
## <a name="remarks"></a>Poznámky  
 Tato hodnota je předaná hostitele do common language runtime (CLR) podle pomocí volání do [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
