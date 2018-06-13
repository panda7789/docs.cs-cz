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
ms.openlocfilehash: da6462a320b1f090940473f566ade91d36e74780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431698"
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE – rozhraní
Slouží jako enumerátor pro atributy objektu kódu v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Získá ukazatele rozhraní na nový `IEnumIDENTITY_ATTRIBUTE` obsahující členy stejné jako to `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Zapíše data obsažená v elementech tohoto `IEnumIDENTITY_ATTRIBUTE` do vyrovnávací paměti zadaná data.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Získá zadaný počet atributů, počínaje na aktuální pozici.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Ukazatel instrukce přesune na začátku tohoto `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Ukazatel instrukce dál přesune o zadaný počet elementů, počínaje na aktuální pozici.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
