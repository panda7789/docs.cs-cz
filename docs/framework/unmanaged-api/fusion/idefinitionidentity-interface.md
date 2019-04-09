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
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192664"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity – rozhraní
Představuje jedinečný podpis kódu, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Získá ukazatel rozhraní na nový `IDefinitionIdentity` objekt, který je totožný s tím `IDefinitionIdentity`, s výjimkou změn zadaného atributu.|  
|`IDefinitionIdentity::EnumAttributes`|Získá ukazatel rozhraní k [ienumidentity_attribute –](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objekt obsahující atributy přidružené k tomuto `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.|  
|`IDefinitionIdentity::SetAttribute`|Nastaví atribut, který má zadaný název v určeném oboru názvů se zadanou hodnotou.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
