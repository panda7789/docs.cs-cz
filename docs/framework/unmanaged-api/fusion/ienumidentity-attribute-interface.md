---
title: "IEnumIDENTITY_ATTRIBUTE – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc77f2106f5063b8db25f375c354a15f9f936e78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
