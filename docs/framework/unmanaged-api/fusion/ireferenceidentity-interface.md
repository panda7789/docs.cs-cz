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
ms.openlocfilehash: bb8686342b20bd6afe0a4c4803d64428ed95c98b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665770"
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
