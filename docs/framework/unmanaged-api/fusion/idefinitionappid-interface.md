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
ms.openlocfilehash: 5bd705ef549de3a8018efe731ef8735ef7b6b915
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083176"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId – rozhraní
Představuje jedinečný identifikátor pro kód, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Získá formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_Codebase`|Nastaví kód tohoto `IDefinitionAppId` objekt do zadané řetězcové hodnoty ve formátu.|  
|`IDefinitionAppId::EnumAppPath`|Získá ukazatel rozhraní k [ienumdefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objekt, který obsahuje sestavení v aktuální cestě aplikace.|  
|`IDefinitionAppId::SetAppPath`|Nastaví cestu k aplikaci pro sestavení v aktuálním oboru na hodnotu odkazuje zadaný [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objektu.|  
|`IDefinitionAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru token pro přihlášení k odběru této `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_SubscriptionId`|Nastaví identifikátor token pro přihlášení k odběru této `IDefinitionAppId` zadaná řetězcová hodnota objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
