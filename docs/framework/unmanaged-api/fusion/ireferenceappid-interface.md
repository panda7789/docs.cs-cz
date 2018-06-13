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
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429514"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId – rozhraní
Představuje odkaz na jedinečný identifikátor pro aplikaci v aktuálním oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Získá ukazatel na řetězcovou reprezentaci identifikátor kódu pro aplikaci odkazuje toto `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Nastaví identifikátor kódu pro aplikace, které odkazuje toto `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Získá ukazatele rozhraní k `IEnumReferenceIdentity` obsahující instance `IReferenceIdentity` instancí, které představují členy této `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Získá ukazatel na řetězcová reprezentace identifikátoru tokenu pro toto předplatné `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Nastaví identifikátor tokenu pro přihlášení k odběru do tohoto `IReferenceAppId` zadaným řetězcem.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
