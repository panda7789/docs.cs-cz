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
ms.openlocfilehash: 692ac4ef4fe8ea64c6a63dc2f02cc04244a842c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432521"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority – rozhraní
Spravuje klíče identity pro objekty kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Získá hodnotu, která určuje, zda jsou obě zadané [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance jsou stejné.|  
|`IIdentityAuthority::AreReferencesEqual`|Získá hodnotu, která určuje, zda jsou obě zadané [ireferenceidentity –](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) instance jsou stejné.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Získá hodnotu, která určuje, zda jsou dvě zadané řetězcové vyjádření identity definice stejné.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Získá hodnotu, která určuje, zda jsou dvě zadané řetězcové vyjádření identity odkaz stejné.|  
|`IIdentityAuthority::CreateDefinition`|Získá ukazatel na nový `IDefinitionIdentity` instance, který představuje objekt kódu v aktuálním oboru.|  
|`IIdentityAuthority::CreateReference`|Získá ukazatel na nový `IReferenceIdentity` instance, který představuje objekt kódu v aktuálním oboru.|  
|`IIdentityAuthority::DefinitionToText`|Získá verzi formátovaný řetězec zadaného `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Vyplní celé zadaný znak široké vyrovnávací paměti s verzí řetězce zadaného `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Získá hodnotu, která určuje, zda zadaný `IDefinitionIdentity` a `IReferenceIdentity` instance odkazovat na stejný objekt kódu.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Získá hodnotu, která určuje, zda zadaný řetězce odkazovat na stejný objekt kódu.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Získá ukazatel na nově vytvořený řetězec klíč pro zadané `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Získá ukazatel na nově vytvořený řetězec klíč pro zadané `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Získá hodnotu hash pro zadaný `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Získá hodnotu hash pro zadaný `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Získá verzi formátovaný řetězec zadaného `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Vyplní celé zadaný znak široké vyrovnávací paměti s verzí řetězce zadaného `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Získá ukazatele rozhraní k `IDefinitionIdentity` instance generované ze zadaného řetězec ve formátu.|  
|`IIdentityAuthority::TextToReference`|Získá ukazatele rozhraní k `IReferenceIdentity` instance generované ze zadaného řetězec ve formátu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
