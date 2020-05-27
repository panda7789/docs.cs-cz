---
title: IGCHost – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805220"
---
# <a name="igchost-interface"></a>IGCHost – rozhraní
Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.  
  
> [!NOTE]
> Počínaje .NET Framework 4,5 lze pomocí metody [IGCHost2 –:: SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) nastavit velikost segmentu uvolňování paměti a maximální velikost 0. generace systému uvolňování paměti na hodnoty větší, než je `DWORD` limit, který je určen metodou [SetGCStartupLimits –](igchost-setgcstartuplimits-method.md) .  
  
> [!NOTE]
> Toto rozhraní je jenom pro odborné použití. Může ovlivnit výkon aplikace, pokud se používá nesprávně.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Collect – metoda](igchost-collect-method.md)|Vynutí, aby se kolekce stala pro danou generaci, bez ohledu na stav aktuálního uvolňování paměti.|  
|[GetStats – metoda](igchost-getstats-method.md)|Získá statistiku pro aktuální stav systému uvolňování paměti.|  
|[GetThreadStats – metoda](igchost-getthreadstats-method.md)|Načte statistiku jednotlivých vláken pro uvolňování paměti.|  
|[SetGCStartupLimits – metoda](igchost-setgcstartuplimits-method.md)|Nastaví velikost segmentu a maximální velikost pro generaci 0.|  
|[SetVirtualMemLimit – metoda](igchost-setvirtualmemlimit-method.md)|Nastaví maximální velikost virtuální paměti modulu runtime.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](corruntimehost-coclass.md)
