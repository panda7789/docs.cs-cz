---
title: "ICorPublishProcess – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 765be4e0ae7657d169ea561bc6a36bcf8cc11153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocess-interface"></a>ICorPublishProcess – rozhraní
Poskytuje metody, která přistupují k zobrazit informace o procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumAppDomains – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|Získá [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která obsahuje aplikační domény v procesu odkazuje toto `ICorPublishProcess`.|  
|[GetDisplayName – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|Získá úplnou cestu ke spustitelnému souboru procesu, který odkazuje toto `ICorPublishProcess`.|  
|[GetProcessID – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.|  
|[IsManaged – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|Získá hodnotu, která určuje, jestli proces odkazuje toto `ICorPublishProcess` je známé, aby byl spuštěn spravovaného kódu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
