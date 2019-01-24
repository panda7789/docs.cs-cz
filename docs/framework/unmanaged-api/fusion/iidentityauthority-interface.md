---
title: IIdentityAuthority – rozhraní
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab8965ca5d6c9c96cea5f5b351547ce2d4dfacc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546277"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority – rozhraní
Spravuje klíče identity pro objekty kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Získá hodnotu, která udává, zda dvě zadat [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instancí jsou si rovny.|  
|`IIdentityAuthority::AreReferencesEqual`|Získá hodnotu, která udává, zda dvě zadat [ireferenceidentity –](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instancí jsou si rovny.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Získá hodnotu určující, zda jsou dvě zadané řetězcové vyjádření identity definice stejné.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Získá hodnotu, která určuje, zda dvě zadané řetězcové vyjádření identity odkazu jsou stejné.|  
|`IIdentityAuthority::CreateDefinition`|Získá ukazatel na novou `IDefinitionIdentity` instanci, která představuje objekt kódu v aktuálním oboru.|  
|`IIdentityAuthority::CreateReference`|Získá ukazatel na novou `IReferenceIdentity` instanci, která představuje objekt kódu v aktuálním oboru.|  
|`IIdentityAuthority::DefinitionToText`|Získá verzi formátovaný řetězec zadaného `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Vyplní vyrovnávací paměti zadaná široký znak s verzí řetězce zadaného `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Získá hodnotu určující, zda zadaný `IDefinitionIdentity` a `IReferenceIdentity` instance odkazují na stejný objekt kódu.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu určující, zda jsou zadané řetězce odkazují na stejný objekt kódu.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Získá ukazatel na nově vytvořený řetězec klíče pro zadaný rozbočovač `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Získá ukazatel na nově vytvořený řetězec klíče pro zadaný rozbočovač `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Získá hodnotu hash pro zadaná `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Získá hodnotu hash pro zadaná `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Získá verzi formátovaný řetězec zadaného `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Vyplní vyrovnávací paměti zadaná široký znak s verzí řetězce zadaného `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Získá ukazatel rozhraní k `IDefinitionIdentity` instance generované ze zadané ve formátu řetězce.|  
|`IIdentityAuthority::TextToReference`|Získá ukazatel rozhraní k `IReferenceIdentity` instance generované ze zadané ve formátu řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
