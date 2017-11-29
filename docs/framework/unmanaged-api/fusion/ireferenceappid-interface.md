---
title: "IReferenceAppId – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Ienumreferenceidentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [Ireferenceidentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
