---
title: "WAITORTIMERCALLBACK – ukazatel na funkci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAITORTIMERCALLBACK
api_location: mscoree.dll
api_type: COM
f1_keywords: WAITORTIMERCALLBACK
helpviewer_keywords: WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f39c023c6911ca0bcc6b62a562785c069d846d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK – ukazatel na funkci
Odkazuje na funkci, která upozorní na hostitele, počkejte zpracování (<xref:System.Threading.WaitHandle>) buď byla signál nebo vypršel časový limit.  
  
 Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpParameter`  
 [v] Ukazatel na objekt, který obsahuje informace definované pro hostitele.  
  
 `TimerOrWaitFired`  
 [v] `true` Pokud popisovač čekání vypršení časového limitu, nebo `false` Pokud byl signál.  
  
## <a name="remarks"></a>Poznámky  
 Funkce, ke kterému `WAITORTIMERCALLBACK` body je funkce zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorWks.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
