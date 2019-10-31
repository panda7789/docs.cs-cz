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
ms.openlocfilehash: 1305b9ebe3cd87ba002ee87610ff309d015a44e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131750"
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity – rozhraní
Slouží jako enumerátor pro kolekci `IReferenceIdentity` objektů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Získá ukazatel rozhraní na nový `IEnumReferenceIdentity`, který obsahuje stejné členy jako tento `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Získá zadaný počet `IReferenceIdentity` objektů, počínaje aktuální pozicí.|  
|`IEnumReferenceIdentity::Reset`|Přesune ukazatel na instrukci na začátek tohoto `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IReferenceIdentity – rozhraní](ireferenceidentity-interface.md)
