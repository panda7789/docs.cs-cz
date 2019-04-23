---
title: COR_PRF_SNAPSHOT_INFO – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa85fb2cebb47ecbd7b0f091cb79f6ea0936b1cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177837"
---
# <a name="corprfsnapshotinfo-enumeration"></a>COR_PRF_SNAPSHOT_INFO – výčet
Určuje, kolik předání dat zpět se snímek zásobníku v každé volání profileru [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkce.  
  
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
|`COR_PRF_SNAPSHOT_DEFAULT`|Označuje, že hodnoty musí být předán pro všechny `StackSnapshotCallback` parametrů, s výjimkou `context` parametru.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Označuje, že hodnoty musí být předán pro všechny `StackSnapshotCallback` parametry, včetně `context` parametru.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Označuje, že se použije jednodušší a alternativní algoritmus procházení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které jsou k dispozici v `COR_PRF_SNAPSHOT_INFO` výčtu jsou předány jako parametry [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
