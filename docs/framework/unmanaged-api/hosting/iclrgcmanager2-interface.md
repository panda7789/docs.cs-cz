---
title: "ICLRGCManager2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2
helpviewer_keywords: ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b025ec31e3797fec3ac184929f1274cb5f68501b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 – rozhraní
Poskytuje metody, které umožňují hostitele k interakci s systém kolekce paměti modul common language runtime.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Setgcstartuplimitsex – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|Nastaví velikost segment kolekce paměti a maximální velikost systém kolekce paměti generace 0. Umožňuje 0. generace a velikost segmentu větší než `DWORD`.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní dědí z [iclrgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
 Modul CLR (CLR) implementuje mechanismus kolekce jeho paměti s spravovaný <xref:System.GC> typu. Další informace o systém kolekce paměti najdete v tématu [uvolňování paměti](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Automatická správa paměti](../../../../docs/standard/automatic-memory-management.md)  
 [Cor_gc_stats – struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [Iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
