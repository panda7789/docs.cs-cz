---
title: IEnumIDENTITY_ATTRIBUTE – rozhraní
ms.date: 03/30/2017
api_name:
- IEnumIDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords:
- IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb3ac150ebfe9fe3698427d8bb2bfb3e3347c07
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796464"
---
# <a name="ienumidentity_attribute-interface"></a>IEnumIDENTITY_ATTRIBUTE – rozhraní
Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Získá ukazatel rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` , který obsahuje stejné členy jako to. `IEnumIDENTITY_ATTRIBUTE`|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Zapíše data obsažená v prvcích tohoto `IEnumIDENTITY_ATTRIBUTE` typu do zadané datové vyrovnávací paměti.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Získá zadaný počet atributů od aktuální pozice.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Přesune ukazatel na instrukci na začátek tohoto `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Přesune ukazatel na instrukci směrem nahoru o zadaný počet prvků od aktuální pozice.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
