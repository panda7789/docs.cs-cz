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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108029"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity – rozhraní
Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Získá ukazatel rozhraní na nový objekt `IDefinitionIdentity`, který je totožný s tímto `IDefinitionIdentity`, s výjimkou zadaných změn atributů.|  
|`IDefinitionIdentity::EnumAttributes`|Získá ukazatel rozhraní na objekt [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , který obsahuje atributy přidružené k tomuto `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.|  
|`IDefinitionIdentity::SetAttribute`|Nastaví atribut, který má zadaný název v zadaném oboru názvů na zadanou hodnotu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
