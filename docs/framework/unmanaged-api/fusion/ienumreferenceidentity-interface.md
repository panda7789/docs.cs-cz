---
title: IEnumReferenceIdentity – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumReferenceIdentity
helpviewer_keywords:
- IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ebc9fe36955bac8b93ec95e9a55fc8ac1197d9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429118"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity – rozhraní
Slouží jako enumerátor pro kolekci `IReferenceIdentity` objekty.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Získá ukazatele rozhraní na nový `IEnumReferenceIdentity` obsahující členy stejné jako to `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Získá zadaný počet `IReferenceIdentity` objektů, počínaje na aktuální pozici.|  
|`IEnumReferenceIdentity::Reset`|Ukazatel instrukce přesune na začátku tohoto `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
