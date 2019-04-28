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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760166"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager – rozhraní
Poskytuje metody, které umožňují common language runtime (CLR) k podání žádostí o virtuální paměti prostřednictvím hostitele, namísto použití standardních funkcí virtuální paměti systému Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR (CLR) získal zadaná paměťová z operačního systému.|  
|[CreateMAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Získá ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která slouží k vyžádání přidělení paměti z haldy vytvořené hostitele.|  
|[GetMemoryLoad – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Získá velikost fyzické paměti, která je aktuálně používán; podle hostitele.|  
|[NeedsVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Upozorňuje hostitele, že modul CLR bude pokus o použití zadaná paměťová.|  
|[RegisterMemoryNotificationCallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele oznámit CLR aktuálního zatížení paměti v počítači.|  
|[ReleasedVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Upozorňuje hostitele, že pomocí zadané paměti modulu CLR byla dokončena.|  
|[VirtualAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, který rezervuje nebo potvrdí změny v oblasti stránek v virtuálního adresového prostoru volajícího procesu.|  
|[VirtualFree – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, který uvolní, rozváže, nebo uvolní a rozváže oblast stránky v rámci virtuálního adresového prostoru volajícího procesu.|  
|[VirtualProtect – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, která změní ochrany v oblasti potvrzené stránek v virtuálního adresového prostoru volajícího procesu.|  
|[VirtualQuery – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, který načte informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostMemoryManager` také poskytuje metody pro CLR získat ukazatel, pomocí kterého k podání žádostí o paměti v haldě a úroveň zatížení paměti v procesu, jak je hlásí hostitele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
