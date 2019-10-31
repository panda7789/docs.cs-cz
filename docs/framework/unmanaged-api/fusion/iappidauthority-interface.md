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
ms.openlocfilehash: 004e4f70e3385e7a71c356cce38e64d0253dcfa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127124"
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
|`IAppIdAuthority::CreateDefinition`|Získá ukazatel rozhraní na nově generovanou instanci `IDefinitionAppId`, která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::CreateReference`|Získá ukazatel rozhraní na nově vytvořenou `IReferenceAppId`, která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::DefinitionToText`|Získá verzi řetězce zadaného `IDefinitionAppId`pomocí zadaných hodnot příznaku.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která označuje, zda zadané `IDefinitionAppId` a `IReferenceAppId` představovat stejné sestavení.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Načte hodnotu, která označuje, jestli zadaný řetězec definice a referenční řetězec představuje stejné sestavení.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Získá klíč řetězce, který představuje zadanou instanci `IDefinitionAppId`.|  
|`IAppIdAuthority::GenerateReferenceKey`|Získá klíč řetězce, který představuje zadanou instanci `IReferenceAppId`.|  
|`IAppIdAuthority::HashDefinition`|Získá klíč hash pro zadanou instanci `IDefinitionAppId`.|  
|`IAppIdAuthority::HashReference`|Získá klíč hash pro zadanou instanci `IReferenceAppId`.|  
|`IAppIdAuthority::ReferenceToText`|Získá verzi řetězce zadaného `IReferenceAppId`pomocí zadaných hodnot příznaku.|  
|`IAppIdAuthority::TextToDefinition`|Získá ukazatel rozhraní `IDefinitionAppId` instance, která představuje sestavení odkazované zadaným řetězcovým klíčem.|  
|`IAppIdAuthority::TextToReference`|Získá ukazatel rozhraní `IReferenceAppId` instance, která představuje sestavení odkazované zadaným řetězcovým klíčem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
