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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131651"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId – rozhraní
Představuje odkaz na jedinečný identifikátor aplikace v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikaci, na kterou odkazuje tento `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Nastaví identifikátor kódu pro aplikaci, na kterou odkazuje tento `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Získá ukazatel rozhraní na instanci `IEnumReferenceIdentity` obsahující `IReferenceIdentity` instance, které reprezentují členy tohoto `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru tokenu pro odběr tohoto `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro odběr tohoto `IReferenceAppId` na zadanou hodnotu řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](fusion-interfaces.md)
- [IEnumReferenceIdentity – rozhraní](ienumreferenceidentity-interface.md)
- [IReferenceIdentity – rozhraní](ireferenceidentity-interface.md)
