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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127095"
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
|`IIdentityAuthority::CreateDefinition`|Získá ukazatel na novou instanci `IDefinitionIdentity`, která představuje objekt kódu v aktuálním oboru.|
|`IIdentityAuthority::CreateReference`|Získá ukazatel na novou instanci `IReferenceIdentity`, která představuje objekt kódu v aktuálním oboru.|
|`IIdentityAuthority::DefinitionToText`|Získá naformátovanou verzi řetězce zadaného `IDefinitionIdentity`.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Vyplní zadanou vyrovnávací paměť s velkým znakem ve verzi řetězce zadaného `IDefinitionIdentity`.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která označuje, zda zadané instance `IDefinitionIdentity` a `IReferenceIdentity` odkazují na stejný objekt kódu.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu, která označuje, zda zadané řetězce odkazují na stejný objekt kódu.|
|`IIdentityAuthority::GenerateDefinitionKey`|Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IDefinitionIdentity`.|
|`IIdentityAuthority::GenerateReferenceKey`|Získá ukazatel na nově vytvořený klíč řetězce pro zadaný `IReferenceIdentity`.|
|`IIdentityAuthority::HashDefinition`|Získá hodnotu hash zadaného `IDefinitionIdentity`.|
|`IIdentityAuthority::HashReference`|Získá hodnotu hash zadaného `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToText`|Získá naformátovanou verzi řetězce zadaného `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Vyplní zadanou vyrovnávací paměť s velkým znakem ve verzi řetězce zadaného `IReferenceIdentity`.|
|`IIdentityAuthority::TextToDefinition`|Získá ukazatel rozhraní na instanci `IDefinitionIdentity` generovanou ze zadaného formátovaného řetězce.|
|`IIdentityAuthority::TextToReference`|Získá ukazatel rozhraní na instanci `IReferenceIdentity` generovanou ze zadaného formátovaného řetězce.|

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).

**Hlavička:** Izolace. h

**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
