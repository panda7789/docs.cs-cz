---
title: COR_PRF_GC_GENERATION – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: d01b864be231e5b0a3fd72dc2f3636a87c8cae83
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448625"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION – výčet
Identifies a garbage-collection generation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|The object is stored as generation 0.|  
|`COR_PRF_GC_GEN_1`|The object is stored as generation 1.|  
|`COR_PRF_GC_GEN_2`|The object is stored as generation 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|The object is stored in the large-object heap.|  
  
## <a name="remarks"></a>Poznámky  
 The garbage collector improves memory management performance by dividing objects into generations based on age. The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects. Objects whose size is larger than a particular value are stored in the large-object heap. Other allocated objects start out belonging to generation 0. All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1. Objects that exist after garbage collection occurs in generation 1 move into generation 2.  
  
 The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.  
  
 The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
