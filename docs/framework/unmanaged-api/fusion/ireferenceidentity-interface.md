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
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity – rozhraní
Představuje odkaz na jedinečný podpis objekt kódu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Získá ukazatele rozhraní na nový `IReferenceIdentity` instanci, která je stejná jako to `IReferenceIdentity`, s výjimkou změny zadaného atributu.|  
|`IReferenceIdentity::EnumAttributes`|Získá ukazatele rozhraní k `IEnumIDENTITY_ATTRIBUTE` instanci, která obsahuje atributy přidružené k tomuto `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Získá hodnotu atributu v určeném oboru názvů se zadaným názvem.|  
|`IReferenceIdentity::SetAttribute`|Nastaví atribut, který má zadaný obor názvů a zadaný název se zadanou hodnotou.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
