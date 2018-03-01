---
title: "IReferenceIdentity – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c9696687f292d7dcaa3d430c1e269f0fedb05e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
