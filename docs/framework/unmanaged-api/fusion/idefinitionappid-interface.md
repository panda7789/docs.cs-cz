---
title: "IDefinitionAppId – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId – rozhraní
Představuje jedinečný identifikátor pro kód, který definuje aplikace v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Získá formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_Codebase`|Nastaví kód to `IDefinitionAppId` objekt do zadané řetězcové hodnoty ve formátu.|  
|`IDefinitionAppId::EnumAppPath`|Získá ukazatele rozhraní k [ienumdefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objekt, který obsahuje sestavení v aktuální cestě aplikace.|  
|`IDefinitionAppId::SetAppPath`|Nastaví cestu k aplikaci pro sestavení v aktuálním oboru na hodnotu odkazuje zadaný [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objektu.|  
|`IDefinitionAppId::get_SubscriptionId`|Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IDefinitionAppId` objekt, který chcete je zadaná řetězcová hodnota.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
