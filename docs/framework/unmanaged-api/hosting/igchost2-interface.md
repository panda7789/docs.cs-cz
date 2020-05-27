---
title: IGCHost2 – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805180"
---
# <a name="igchost2-interface"></a>IGCHost2 – rozhraní
Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.  
  
> [!NOTE]
> Pro nové vývojové prostředí doporučujeme místo toho použít rozhraní [ICLRGCManager2 –](iclrgcmanager2-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetGCStartupLimitsEx – metoda](igchost2-setgcstartuplimitsex-method.md)|Nastaví velikost segmentu a maximální velikost pro generaci 0. Povoluje generaci 0 a velikosti segmentů větší než `DWORD` .|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Rozhraní hostování CLR](clr-hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](corruntimehost-coclass.md)
