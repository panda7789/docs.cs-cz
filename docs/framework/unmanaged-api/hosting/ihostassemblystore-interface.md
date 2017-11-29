---
title: "IHostAssemblyStore – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore – rozhraní
Poskytuje metody, které umožňují hostitele k načtení sestavení a moduly nezávisle na modul CLR (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Provideassembly – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|Získá odkaz na sestavení, které se odkazuje [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) vrácená z volání [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).|  
|[Providemodule – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|Přeloží modulu v sestavení nebo propojené souboru prostředků (nikoli vložené).|  
  
## <a name="remarks"></a>Poznámky  
 `IHostAssemblyStore`poskytuje způsob pro hostitele k načtení sestavení efektivně podle identity sestavení. Hostitel načte sestavení vrácením `IStream` instancí, které bod přímo na bajty.  
  
 Modul CLR Určuje, zda hostitel implementovala `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci. To umožňuje hostiteli, například k řízení vazba k sestavení uživatele, ale závisí na modulu runtime pro vazbu na sestavení rozhraní .NET Framework.  
  
> [!NOTE]
>  Při poskytování implementace `IHostAssemblyStore`, hostitele určuje jeho záměr vyřešit všechny sestavení, které nejsou odkazuje `ICLRAssemblyReferenceList` vrácená z `IHostAssemblyManager::GetNonHostStoreAssemblies`.  
  
> [!NOTE]
>  Rozhraní .NET Framework verze 2.0 neposkytuje způsob, jak na hostiteli a načíst nativní bitové kopie sestavení, protože poskytované [generátor (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nástroj.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrassemblyreferencelist – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [Ihostassemblymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
