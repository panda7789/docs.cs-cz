---
title: IReferenceAppId – rozhraní
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796365"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId – rozhraní
Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikaci, na kterou se odkazuje `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Nastaví identifikátor kódu aplikace, na kterou se odkazuje `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Získá ukazatel rozhraní na `IEnumReferenceIdentity` instanci `IReferenceIdentity` obsahující instance `IReferenceAppId`, které reprezentují členy.|  
|`IReferenceAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro odběr `IReferenceAppId` na zadanou hodnotu řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IEnumReferenceIdentity – rozhraní](ienumreferenceidentity-interface.md)
- [IReferenceIdentity – rozhraní](ireferenceidentity-interface.md)
