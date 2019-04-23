---
title: IReferenceIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd46ea26532074c9ea42da4d07a38ed583aad076
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220159"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity – rozhraní
Představuje odkaz na jedinečný podpis kódu objektu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Získá ukazatel rozhraní na nový `IReferenceIdentity` instanci, která se shoduje s tím `IReferenceIdentity`, s výjimkou změn zadaného atributu.|  
|`IReferenceIdentity::EnumAttributes`|Získá ukazatel rozhraní k `IEnumIDENTITY_ATTRIBUTE` instance, která obsahuje atributy přidružené k tomuto `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.|  
|`IReferenceIdentity::SetAttribute`|Nastaví atribut, který má zadaný obor názvů a zadaným názvem se zadanou hodnotou.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
