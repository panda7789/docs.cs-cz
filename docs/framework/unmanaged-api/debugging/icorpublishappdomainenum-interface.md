---
title: "ICorPublishAppDomainEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum
helpviewer_keywords: ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f84a93053744f059eb3fdd06e2fb69e098e24ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenum-interface"></a>ICorPublishAppDomainEnum – rozhraní
Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objekty, které aktuálně existovat v rámci procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|Získá zadaný počet `ICorPublishAppDomain` instancí z kolekce, počínaje na aktuální pozici.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorPublishAppDomainEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [CorpubPublish – třída typu coclass](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
