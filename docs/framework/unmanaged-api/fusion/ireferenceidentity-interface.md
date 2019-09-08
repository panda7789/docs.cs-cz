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
ms.openlocfilehash: 2bb151d7c77104d8e24acefaac2e1f109b67f168
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796353"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity – rozhraní
Představuje odkaz na jedinečný podpis objektu kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Získá ukazatel rozhraní na novou `IReferenceIdentity` instanci, která je stejná jako tato `IReferenceIdentity`, s výjimkou změny zadaného atributu.|  
|`IReferenceIdentity::EnumAttributes`|Získá ukazatel rozhraní na `IEnumIDENTITY_ATTRIBUTE` instanci, která obsahuje atributy přidružené k tomuto. `IReferenceIdentity`|  
|`IReferenceIdentity::GetAttribute`|Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.|  
|`IReferenceIdentity::SetAttribute`|Nastaví atribut, který má zadaný obor názvů a zadaný název na zadanou hodnotu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE – rozhraní](ienumidentity-attribute-interface.md)
