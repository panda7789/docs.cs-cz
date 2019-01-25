---
title: ICLRGCManager2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9897526882a8ae53410a7744f78c558dfa6981e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708581"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 – rozhraní
Poskytuje metody, které povolí hostitelské pracovat s common language runtime uvolňování paměti kolekce systému.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetGCStartupLimitsEx – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|Nastaví velikost segmentu kolekce uvolnění paměti a maximální velikost systému kolekce uvolnění paměti generace 0. Umožňuje 0. generace a větší velikosti segmentů `DWORD`.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní se dědí z [iclrgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
 Modul CLR (CLR) implementuje mechanismus jeho uvolňování paměti kolekce s spravovanou <xref:System.GC> typu. Další informace o systému uvolňování paměti kolekce najdete v tématu [uvolňování](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Automatická správa paměti](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS – struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
