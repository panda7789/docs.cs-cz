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
ms.openlocfilehash: cca73eec663b9afd12ecea5ab9d7073ea0168d33
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501553"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore – rozhraní
Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[ProvideAssembly – metoda](ihostassemblystore-provideassembly-method.md)|Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , vrácený voláním metody [IHostAssemblyManager:: GetNonHostStoreAssemblies –](ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[ProvideModule – metoda](ihostassemblystore-providemodule-method.md)|Vyřeší modul v rámci sestavení nebo propojeného (nevloženého) souboru prostředků.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostAssemblyStore`poskytuje způsob, jak může hostitel načíst sestavení efektivně na základě identity sestavení. Hostitel načte sestavení vrácením `IStream` instancí, které odkazují přímo na bajty.  
  
 CLR určuje, zda je hostitel implementovaný `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci. To umožňuje hostiteli, například k řízení vazby na sestavení uživatelů, ale k tomu, aby se spoléhá na to, že modul runtime vytvoří vazbu na .NET Framework sestavení.  
  
> [!NOTE]
> V rámci poskytování implementace `IHostAssemblyStore` , hostitel Určuje svůj záměr na překlad všech sestavení, na která neodkazuje `ICLRAssemblyReferenceList` vrácená z `IHostAssemblyManager::GetNonHostStoreAssemblies` .  
  
> [!NOTE]
> .NET Framework verze 2,0 neposkytuje způsob, jak hostitel načíst nativní bitovou kopii sestavení, jak poskytuje nástroj [generátor nativních bitových kopií (Ngen. exe)](../../tools/ngen-exe-native-image-generator.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
