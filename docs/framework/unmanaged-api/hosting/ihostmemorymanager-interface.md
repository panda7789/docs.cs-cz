---
title: IHostMemoryManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: 4e7e76a4a3ab291ee97ad0912e3d6224cdf96fba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804489"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) provádět požadavky na virtuální paměť prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace – metoda](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR (Common Language Runtime) získal zadanou paměť z operačního systému.|  
|[CreateMAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Získá ukazatel rozhraní na instanci [IHostMalloc](ihostmalloc-interface.md) , která se používá k vyžádání přidělení paměti z haldy vytvořené hostitelem.|  
|[GetMemoryLoad – metoda](ihostmemorymanager-getmemoryload-method.md)|Načte velikost fyzické paměti, která je aktuálně používána, jak je uvedeno v hostiteli.|  
|[NeedsVirtualAddressSpace – metoda](ihostmemorymanager-needsvirtualaddressspace-method.md)|Upozorní hostitele, že se bude modul CLR pokoušet použít zadanou paměť.|  
|[RegisterMemoryNotificationCallback – metoda](ihostmemorymanager-registermemorynotificationcallback-method.md)|Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil CLR na aktuální zatížení paměti v počítači.|  
|[ReleasedVirtualAddressSpace – metoda](ihostmemorymanager-releasedvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR dokončil používání zadané paměti.|  
|[VirtualAlloc – metoda](ihostmemorymanager-virtualalloc-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která rezervuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru volajícího procesu.|  
|[VirtualFree – metoda](ihostmemorymanager-virtualfree-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která vydává, odváže nebo uvolňuje a odváže oblast stránek v rámci virtuálního adresového prostoru volajícího procesu.|  
|[VirtualProtect – metoda](ihostmemorymanager-virtualprotect-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která mění ochranu v oblasti svěřené stránky ve virtuálním adresním prostoru volajícího procesu.|  
|[VirtualQuery – metoda](ihostmemorymanager-virtualquery-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostMemoryManager`poskytuje také metody pro CLR k získání ukazatele, pomocí kterého se vytvářejí požadavky na paměť na haldě, a k získání úrovně paměti v procesu, jak je uvedeno v hostiteli.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IHostMalloc – rozhraní](ihostmalloc-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
