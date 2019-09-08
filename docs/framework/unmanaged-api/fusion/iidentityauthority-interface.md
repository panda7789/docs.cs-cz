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
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796419"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority – rozhraní

Spravuje klíče identity pro objekty kódu.

## <a name="methods"></a>Metody

|Metoda|Popis|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Získá hodnotu, která označuje, zda jsou dvě zadané instance [IDefinitionIdentity –](idefinitionidentity-interface.md) stejné.|
|`IIdentityAuthority::AreReferencesEqual`|Získá hodnotu, která označuje, zda jsou dvě zadané instance [IReferenceIdentity –](ireferenceidentity-interface.md) stejné.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Získá hodnotu, která označuje, zda jsou dva zadané reprezentace identity definice řetězce stejné.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Získá hodnotu, která označuje, zda jsou dva zadané řetězce odkazu na identitu stejné.|
|`IIdentityAuthority::CreateDefinition`|Získá ukazatel na novou `IDefinitionIdentity` instanci, která představuje objekt kódu v aktuálním oboru.|
|`IIdentityAuthority::CreateReference`|Získá ukazatel na novou `IReferenceIdentity` instanci, která představuje objekt kódu v aktuálním oboru.|
|`IIdentityAuthority::DefinitionToText`|Načte formátovanou verzi zadaného `IDefinitionIdentity`řetězce.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Vyplní zadanou vyrovnávací paměť s velkým počtem znaků zadanou `IDefinitionIdentity`verzí řetězce.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která označuje, zda zadané `IDefinitionIdentity` instance `IReferenceIdentity` a odkazují na stejný objekt kódu.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu, která označuje, zda zadané řetězce odkazují na stejný objekt kódu.|
|`IIdentityAuthority::GenerateDefinitionKey`|Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IDefinitionIdentity`objekt.|
|`IIdentityAuthority::GenerateReferenceKey`|Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IReferenceIdentity`objekt.|
|`IIdentityAuthority::HashDefinition`|Načte hodnotu hash zadaného `IDefinitionIdentity`typu.|
|`IIdentityAuthority::HashReference`|Načte hodnotu hash zadaného `IReferenceIdentity`typu.|
|`IIdentityAuthority::ReferenceToText`|Načte formátovanou verzi zadaného `IReferenceIdentity`řetězce.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Vyplní zadanou vyrovnávací paměť s velkým počtem znaků zadanou `IReferenceIdentity`verzí řetězce.|
|`IIdentityAuthority::TextToDefinition`|Získá ukazatel rozhraní na `IDefinitionIdentity` instanci generovanou ze zadaného formátovaného řetězce.|
|`IIdentityAuthority::TextToReference`|Získá ukazatel rozhraní na `IReferenceIdentity` instanci generovanou ze zadaného formátovaného řetězce.|

## <a name="requirements"></a>Požadavky

**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlaviček** Izolace. h

**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
