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
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427266"
---
# <a name="cor_prf_snapshot_info-enumeration"></a>COR_PRF_SNAPSHOT_INFO – výčet
Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce [StackSnapshotCallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Členové|Popis|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback` s výjimkou parametru `context`.|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback`, včetně parametru `context`.|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|Indikuje, že se použije jednodušší algoritmus procházení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty, které jsou poskytovány výčtem `COR_PRF_SNAPSHOT_INFO`, jsou předány jako parametry do metody [DoStackSnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [DoStackSnapshot – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
