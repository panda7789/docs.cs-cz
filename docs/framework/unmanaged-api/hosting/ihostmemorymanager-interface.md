---
title: "IHostMemoryManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager – rozhraní
Poskytuje metody, které povolit modul CLR (CLR) provádět požadavky na virtuální paměti prostřednictvím hostitele, místo použití standardní funkce Win32 virtuální paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Acquiredvirtualaddressspace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Upozorní hostitele, modul CLR (CLR) má získat zadaná paměťová z operačního systému.|  
|[Createmalloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která se používá k požadavku na přidělení paměti ze haldy vytvořené hostitele.|  
|[Getmemoryload – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Získá množství fyzické paměti, který je aktuálně používá, jsou uvedeny pro hostitele.|  
|[Needsvirtualaddressspace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Aby modul CLR bude pokus o použití zadaná paměťová upozorní hostitele.|  
|[Registermemorynotificationcallback – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele oznámit CLR aktuální zatížení paměti v počítači.|  
|[Releasedvirtualaddressspace – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Upozorní hostitele, že pomocí zadaná paměťová modulu CLR byla dokončena.|  
|[VirtualAlloc – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Slouží jako logické obálku pro odpovídající funkci, Win32, která si vyhrazuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru procesu volání.|  
|[Virtualfree – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, což uvolní, decommits, nebo uvolní a decommits oblast stránek ve virtuálním adresním prostoru procesu volání.|  
|[VirtualProtect – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Slouží jako logické obálku pro odpovídající funkci Win32, které změní ochrany v oblasti potvrdit stránek ve virtuálním adresním prostoru procesu volání.|  
|[VirtualQuery – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Slouží jako logické obálku pro odpovídající funkci, Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru procesu volání.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostMemoryManager`také poskytuje metody pro CLR získat ukazatel přes který provádět požadavky na paměť v haldě a získat úroveň přetížení paměti v procesu vykazované hostitele.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ihostmalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
