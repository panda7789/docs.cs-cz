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
ms.openlocfilehash: f878e2f1f86bc42c0ff5abada8d7df4feb9ed228
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504183"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager – rozhraní
Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti modulu CLR.  
  
> [!NOTE]
> Počínaje .NET Framework 4,5 lze pomocí metody [ICLRGCManager2 –:: SetGCStartupLimitsEx –](iclrgcmanager2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší, než je `DWORD` limit, který je určen metodou [SetGCStartupLimits –](iclrgcmanager-setgcstartuplimits-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
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
  
## <a name="see-also"></a>Viz také:

- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS – struktura](cor-gc-stats-structure.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [Rozhraní hostování CLR](clr-hosting-interfaces.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
