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
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796835"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority – rozhraní
Poskytuje metody, které generují a porovnávají klíče pro identity a odkazy aplikací.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Získá hodnotu, která označuje, zda jsou dvě zadané instance [IDefinitionAppId –](idefinitionappid-interface.md) stejné. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.|  
|`IAppIdAuthority::AreReferencesEqual`|Získá hodnotu, která označuje, zda jsou dvě zadané instance [IReferenceAppId –](ireferenceappid-interface.md) stejné. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Získá hodnotu, která označuje, zda jsou dvě zadané definice řetězce stejné. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Získá hodnotu, která označuje, zda jsou dva zadané odkazy na řetězce stejné. Můžete předat hodnotu příznaku IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, která ignoruje jejich příslušné informace o verzi.|  
|`IAppIdAuthority::CreateDefinition`|Získá ukazatel rozhraní na nově vygenerovanou `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::CreateReference`|Získá ukazatel rozhraní na nově vytvořenou `IReferenceAppId` , která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::DefinitionToText`|Načte verzi řetězce zadaného `IDefinitionAppId`pomocí zadaných hodnot příznaku.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která označuje, zda zadané `IDefinitionAppId` a `IReferenceAppId` představující stejné sestavení.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Načte hodnotu, která označuje, jestli zadaný řetězec definice a referenční řetězec představuje stejné sestavení.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Získá klíč řetězce, který představuje zadanou `IDefinitionAppId` instanci.|  
|`IAppIdAuthority::GenerateReferenceKey`|Získá klíč řetězce, který představuje zadanou `IReferenceAppId` instanci.|  
|`IAppIdAuthority::HashDefinition`|Získá klíč hash pro zadanou `IDefinitionAppId` instanci.|  
|`IAppIdAuthority::HashReference`|Získá klíč hash pro zadanou `IReferenceAppId` instanci.|  
|`IAppIdAuthority::ReferenceToText`|Načte verzi řetězce zadaného `IReferenceAppId`pomocí zadaných hodnot příznaku.|  
|`IAppIdAuthority::TextToDefinition`|Získá ukazatel rozhraní na `IDefinitionAppId` instanci, která představuje sestavení odkazované zadaným řetězcovým klíčem.|  
|`IAppIdAuthority::TextToReference`|Získá ukazatel rozhraní na `IReferenceAppId` instanci, která představuje sestavení odkazované zadaným řetězcovým klíčem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
