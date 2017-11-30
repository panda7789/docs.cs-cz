---
title: "IAppIdAuthority – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07bfd26a43d264babc9854b0fd0da909dd329405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority – rozhraní
Poskytuje metody, které generovat a porovnání klíče pro identity aplikace a odkazy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Získá hodnotu, která určuje, zda jsou obě zadané [idefinitionappid –](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instance jsou stejné. Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.|  
|`IAppIdAuthority::AreReferencesEqual`|Získá hodnotu, která určuje, zda jsou obě zadané [ireferenceappid –](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instance jsou stejné. Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Získá hodnotu, která určuje, zda jsou si rovny dvě definice zadaný řetězec. Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Získá hodnotu, která určuje, zda jsou dva odkazy zadaný řetězec stejné. Může předat hodnotu příznak IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorovat své informace odpovídající verze.|  
|`IAppIdAuthority::CreateDefinition`|Získá ukazatele rozhraní k nově vygenerovaný `IDefinitionAppId` instanci, která představuje sestavení v aktuálním oboru.|  
|`IAppIdAuthority::CreateReference`|Získá ukazatele rozhraní pro nově vytvořený `IReferenceAppId` představující sestavení v aktuálním oboru.|  
|`IAppIdAuthority::DefinitionToText`|Získá řetězec verze zadaného `IDefinitionAppId`, pomocí zadaný příznak hodnot.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která určuje, zda zadaný `IDefinitionAppId` a `IReferenceAppId` představují do stejného sestavení.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu, která určuje, zda jsou určená definice řetězec a odkaz na řetězec představují do stejného sestavení.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Získá řetězec klíč, který představuje zadaný `IDefinitionAppId` instance.|  
|`IAppIdAuthority::GenerateReferenceKey`|Získá řetězec klíč, který představuje zadaný `IReferenceAppId` instance.|  
|`IAppIdAuthority::HashDefinition`|Získá klíč algoritmu hash pro zadaná `IDefinitionAppId` instance.|  
|`IAppIdAuthority::HashReference`|Získá klíč algoritmu hash pro zadaná `IReferenceAppId` instance.|  
|`IAppIdAuthority::ReferenceToText`|Získá řetězec verze zadaného `IReferenceAppId`, pomocí zadaný příznak hodnot.|  
|`IAppIdAuthority::TextToDefinition`|Získá ukazatele rozhraní k `IDefinitionAppId` instanci, která představuje sestavení odkazuje klíč zadaný řetězec.|  
|`IAppIdAuthority::TextToReference`|Získá ukazatele rozhraní k `IReferenceAppId` instanci, která představuje sestavení odkazuje klíč zadaný řetězec.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
