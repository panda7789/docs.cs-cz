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
ms.openlocfilehash: 401c23e44cc473d0a27a82a00343852693cb0f2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity – rozhraní
Představuje jedinečné podpis kód, který definuje aplikace v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Získá ukazatele rozhraní na nový `IDefinitionIdentity` objekt, který je stejný jako to `IDefinitionIdentity`, s výjimkou změny zadaného atributu.|  
|`IDefinitionIdentity::EnumAttributes`|Získá ukazatele rozhraní k [ienumidentity_attribute –](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) objekt obsahující atributy přidružené k tomuto `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Získá hodnotu atributu se zadaným názvem v určeném oboru názvů.|  
|`IDefinitionIdentity::SetAttribute`|Nastaví atribut, který má zadaný název v určeném oboru názvů se zadanou hodnotou.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
