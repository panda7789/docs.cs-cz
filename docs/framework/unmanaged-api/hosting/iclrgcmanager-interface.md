---
title: ICLRGCManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: 76a50be6da790ed7bd193c489d36e2823cdbe587
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616955"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager – rozhraní
Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti modulu CLR.  
  
> [!NOTE]
> Počínaje .NET Framework 4,5 lze pomocí metody [ICLRGCManager2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší, než je `DWORD` limit, který je určen metodou [SetGCStartupLimits –](iclrgcmanager-setgcstartuplimits-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Collect – metoda](iclrgcmanager-collect-method.md)|Vynutí uvolňování paměti pro určenou generaci.|  
|[GetStats – metoda](iclrgcmanager-getstats-method.md)|Získá sadu aktuálních statistik o systému uvolňování paměti.|  
|[SetGCStartupLimits – metoda](iclrgcmanager-setgcstartuplimits-method.md)|Nastaví velikost segmentu uvolňování paměti a maximální velikost generace 0 systému uvolňování paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) implementuje svůj mechanizmus uvolňování paměti se spravovaným <xref:System.GC> typem. Další informace o systému uvolňování paměti naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS – struktura](cor-gc-stats-structure.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [Rozhraní hostování CLR](clr-hosting-interfaces.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
