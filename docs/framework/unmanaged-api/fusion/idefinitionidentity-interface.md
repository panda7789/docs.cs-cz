---
title: IDefinitionIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796525"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity – rozhraní
Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Získá ukazatel rozhraní na nový `IDefinitionIdentity` objekt, který je identický `IDefinitionIdentity`s výjimkou určených změn atributů.|  
|`IDefinitionIdentity::EnumAttributes`|Získá ukazatel rozhraní na objekt [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , který obsahuje atributy přidružené k tomuto `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.|  
|`IDefinitionIdentity::SetAttribute`|Nastaví atribut, který má zadaný název v zadaném oboru názvů na zadanou hodnotu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
