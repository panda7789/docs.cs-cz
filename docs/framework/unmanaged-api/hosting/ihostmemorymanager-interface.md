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
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128651"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager – rozhraní
Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) provádět požadavky na virtuální paměť prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR (Common Language Runtime) získal zadanou paměť z operačního systému.|  
|[CreateMAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) , která se používá k vyžádání přidělení paměti z haldy vytvořené hostitelem.|  
|[GetMemoryLoad – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Načte velikost fyzické paměti, která je aktuálně používána, jak je uvedeno v hostiteli.|  
|[NeedsVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Upozorní hostitele, že se bude modul CLR pokoušet použít zadanou paměť.|  
|[RegisterMemoryNotificationCallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil CLR na aktuální zatížení paměti v počítači.|  
|[ReleasedVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR dokončil používání zadané paměti.|  
|[VirtualAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která rezervuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru volajícího procesu.|  
|[VirtualFree – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která vydává, odváže nebo uvolňuje a odváže oblast stránek v rámci virtuálního adresového prostoru volajícího procesu.|  
|[VirtualProtect – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která mění ochranu v oblasti svěřené stránky ve virtuálním adresním prostoru volajícího procesu.|  
|[VirtualQuery – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Slouží jako logická obálka odpovídající funkce Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostMemoryManager` také poskytuje metody pro CLR k získání ukazatele, pomocí kterého se vytvářejí požadavky na paměť na haldě, a k získání úrovně paměti v procesu, jak je uvedeno v hostiteli.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
