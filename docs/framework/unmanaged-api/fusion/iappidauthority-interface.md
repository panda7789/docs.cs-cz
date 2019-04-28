---
title: IAppIdAuthority – rozhraní
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697573"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority – rozhraní
Poskytuje metody, která generují a porovnat klíče pro identity aplikací a odkazy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Získá hodnotu, která udává, zda dvě zadat [idefinitionappid –](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instancí jsou si rovny. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.|  
|`IAppIdAuthority::AreReferencesEqual`|Získá hodnotu, která udává, zda dvě zadat [ireferenceappid –](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instancí jsou si rovny. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Získá hodnotu určující, zda dvě definice zadaného řetězce jsou stejné. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Získá hodnotu určující, zda jsou dva odkazy zadaného řetězce rovny. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat informace o jejich příslušné verzi.|  
|`IAppIdAuthority::CreateDefinition`|Získá ukazatel rozhraní k nově vygenerovaný `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::CreateReference`|Získá ukazatel rozhraní na nově vytvořený `IReferenceAppId` , která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::DefinitionToText`|Získá řetězec verzi zadaného `IDefinitionAppId`, pomocí hodnot pro zadaný příznak.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Získá hodnotu určující, zda zadaný `IDefinitionAppId` a `IReferenceAppId` představují stejné sestavení.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu určující, zda řetězec zadané definice a odkaz na řetězec představují stejné sestavení.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Získá řetězec klíče, který představuje zadaný `IDefinitionAppId` instance.|  
|`IAppIdAuthority::GenerateReferenceKey`|Získá řetězec klíče, který představuje zadaný `IReferenceAppId` instance.|  
|`IAppIdAuthority::HashDefinition`|Získá hodnotu hash klíče pro zadaný `IDefinitionAppId` instance.|  
|`IAppIdAuthority::HashReference`|Získá hodnotu hash klíče pro zadaný `IReferenceAppId` instance.|  
|`IAppIdAuthority::ReferenceToText`|Získá řetězec verzi zadaného `IReferenceAppId`, pomocí hodnot pro zadaný příznak.|  
|`IAppIdAuthority::TextToDefinition`|Získá ukazatel rozhraní k `IDefinitionAppId` instanci, která představuje sestavení odkazováno klíčem zadaného řetězce.|  
|`IAppIdAuthority::TextToReference`|Získá ukazatel rozhraní k `IReferenceAppId` instanci, která představuje sestavení odkazováno klíčem zadaného řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
