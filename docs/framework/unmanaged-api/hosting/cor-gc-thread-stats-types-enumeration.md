---
title: "COR_GC_THREAD_STATS_TYPES – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS_TYPES
helpviewer_keywords: COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1967f13037be597288b48cbbdf001cad5d6b8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corgcthreadstatstypes-enumeration"></a>COR_GC_THREAD_STATS_TYPES – výčet
Označuje statistiku kolekce paměti na vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|Vlákno má bajtů, které byly povýší v nejnovější uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
