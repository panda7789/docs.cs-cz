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
ms.openlocfilehash: d3edae4cb112f46643734c5f1612d9df36ad47e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441321"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) provádět požadavky na virtuální paměti prostřednictvím hostitele, místo použití standardní funkce Win32 virtuální paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Upozorní hostitele, modul CLR (CLR) má získat zadaná paměťová z operačního systému.|  
|[CreateMAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která se používá k požadavku na přidělení paměti ze haldy vytvořené hostitele.|  
|[GetMemoryLoad – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Získá množství fyzické paměti, který je aktuálně používá, jsou uvedeny pro hostitele.|  
|[NeedsVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Aby modul CLR bude pokus o použití zadaná paměťová upozorní hostitele.|  
|[RegisterMemoryNotificationCallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele oznámit CLR aktuální zatížení paměti v počítači.|  
|[ReleasedVirtualAddressSpace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Upozorní hostitele, že pomocí zadaná paměťová modulu CLR byla dokončena.|  
|[VirtualAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Slouží jako logické obálku pro odpovídající funkci, Win32, která si vyhrazuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru procesu volání.|  
|[VirtualFree – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, což uvolní, decommits, nebo uvolní a decommits oblast stránek ve virtuálním adresním prostoru procesu volání.|  
|[VirtualProtect – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, které změní ochrany v oblasti potvrdit stránek ve virtuálním adresním prostoru procesu volání.|  
|[VirtualQuery – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Slouží jako logické obálku pro odpovídající funkci, Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru procesu volání.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostMemoryManager` také poskytuje metody pro CLR získat ukazatel přes který provádět požadavky na paměť v haldě a získat úroveň přetížení paměti v procesu vykazované hostitele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
