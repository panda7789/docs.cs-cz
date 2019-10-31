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
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108202"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId – rozhraní
Představuje jedinečný identifikátor kódu, který definuje aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Načte formátovaný řetězec, který představuje kód v tomto objektu `IDefinitionAppId`.|  
|`IDefinitionAppId::put_Codebase`|Nastaví kód tohoto objektu `IDefinitionAppId` na zadanou naformátovanou hodnotu řetězce.|  
|`IDefinitionAppId::EnumAppPath`|Získá ukazatel rozhraní na objekt [IEnumDefinitionIdentity –](ienumdefinitionidentity-interface.md) , který obsahuje sestavení v aktuální cestě aplikace.|  
|`IDefinitionAppId::SetAppPath`|Nastaví cestu aplikace pro sestavení v aktuálním rozsahu na hodnotu, na kterou odkazuje zadaný objekt [IDefinitionIdentity –](idefinitionidentity-interface.md) .|  
|`IDefinitionAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto objektu `IDefinitionAppId`.|  
|`IDefinitionAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro odběr tohoto `IDefinitionAppId` objektu na zadanou hodnotu řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
