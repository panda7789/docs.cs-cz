---
title: ICLRMemoryNotificationCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212151"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback – rozhraní
Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí metodiky podobný Win32 `CreateMemoryResourceNotification` funkce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OnMemoryNotification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|Zatížení paměti v počítači upozorní common language runtime (CLR).|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel používá `ICLRMemoryNotificationCallback` rozhraní pro žádosti, že modul CLR uvolnění paměti prostředků.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
