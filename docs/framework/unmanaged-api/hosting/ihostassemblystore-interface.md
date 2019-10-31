---
title: IHostAssemblyStore – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: d7475e2423d4dc6f57e8928514d7991169eef232
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124492"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore – rozhraní
Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ProvideAssembly – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , vrácený voláním metody [IHostAssemblyManager:: GetNonHostStoreAssemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Vyřeší modul v rámci sestavení nebo propojeného (nevloženého) souboru prostředků.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostAssemblyStore` poskytuje způsob, jak může hostitel načíst sestavení efektivně na základě identity sestavení. Hostitel načte sestavení vrácením `IStream` instancí, které přímo odkazují na bajty.  
  
 CLR určuje, zda hostitel implementoval `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci. To umožňuje hostiteli, například k řízení vazby na sestavení uživatelů, ale k tomu, aby se spoléhá na to, že modul runtime vytvoří vazbu na .NET Framework sestavení.  
  
> [!NOTE]
> V rámci poskytování implementace `IHostAssemblyStore`hostitel Určuje svůj záměr na překlad všech sestavení, na která neodkazuje `ICLRAssemblyReferenceList` vrácených z `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
> .NET Framework verze 2,0 neposkytuje způsob, jak hostitel načíst nativní bitovou kopii sestavení, jak poskytuje nástroj [generátor nativních bitových kopií (Ngen. exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
