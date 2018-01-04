---
title: "GetAppIdAuthority – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type: COM
f1_keywords: GetAppIdAuthority
helpviewer_keywords: GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e89624feb04050534b917b865d5cb53b8c4cf58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getappidauthority-function"></a>GetAppIdAuthority – funkce
Získá odkazy [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instanci, která spravuje klíče pro identity aplikace a odkazy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppIAppIdAuthority`  
 [out] Vrácený `IAppIdAuthority` ukazatel.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IAppIdAuthority – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [Globální statické funkce pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
