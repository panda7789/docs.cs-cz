---
title: IDefinitionAppId – rozhraní
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2735355097a1f3f581b3a4bc74f08d8f2ebf3bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
