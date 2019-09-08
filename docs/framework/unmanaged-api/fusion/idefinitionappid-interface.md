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
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796518"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId – rozhraní
Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Načte formátovaný řetězec, který představuje kód v tomto `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_Codebase`|Nastaví kód tohoto `IDefinitionAppId` objektu na zadanou naformátovanou řetězcovou hodnotu.|  
|`IDefinitionAppId::EnumAppPath`|Získá ukazatel rozhraní na objekt [IEnumDefinitionIdentity –](ienumdefinitionidentity-interface.md) , který obsahuje sestavení v aktuální cestě aplikace.|  
|`IDefinitionAppId::SetAppPath`|Nastaví cestu aplikace pro sestavení v aktuálním rozsahu na hodnotu, na kterou odkazuje zadaný objekt [IDefinitionIdentity –](idefinitionidentity-interface.md) .|  
|`IDefinitionAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto `IDefinitionAppId` objektu.|  
|`IDefinitionAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro odběr na tento `IDefinitionAppId` objekt na zadanou hodnotu řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
