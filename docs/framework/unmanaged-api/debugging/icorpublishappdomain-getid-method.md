---
title: "ICorPublishAppDomain::GetID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08d6146c6188e23f0846f51e88484d7f1544aff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomaingetid-method"></a>ICorPublishAppDomain::GetID – metoda
Získá jedinečný identifikátor pro tento [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puId`  
 [out] Ukazatel na identifikátor domény aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Pouze v oboru obsahujícího procesu je jedinečný identifikátor.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorPub.idl, CorPub.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorPublishAppDomain – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
