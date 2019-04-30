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
ms.openlocfilehash: 25733e459423500352595d6be0eee26ef75ca7e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789677"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId – rozhraní
Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Získá ukazatel na řetězcovou reprezentaci identifikátoru kódu pro aplikace, které odkazuje tato `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Nastaví kód identifikátor pro aplikaci odkazovaná tímto objektem `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Získá ukazatel rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy tohoto `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Získá ukazatel na řetězcovou reprezentaci identifikátoru token pro přihlášení k odběru této `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Nastaví identifikátor token pro přihlášení k odběru této `IReferenceAppId` hodnotu zadaného řetězce.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IEnumReferenceIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)
- [IReferenceIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
