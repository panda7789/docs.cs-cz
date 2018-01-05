---
title: "COR_PRF_SNAPSHOT_INFO – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SNAPSHOT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SNAPSHOT_INFO
helpviewer_keywords: COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4573ec44253b1b0f26ae62591db149f0447d3935
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO – výčet
Určuje, kolik předání dat zpět snímkem zásobníku při každém volání do okna profilování [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Členové|Popis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Označuje, že hodnoty musí být předána pro všechny `StackSnapshotCallback` parametrů, s výjimkou `context` parametr.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Označuje, že hodnoty musí být předána pro všechny `StackSnapshotCallback` parametry, včetně `context` parametr.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Označuje, že jednodušší, alternativní algoritmus procházení zásobníku se použije.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které jsou poskytovány `COR_PRF_SNAPSHOT_INFO` výčtu jsou předány jako parametry, které [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
