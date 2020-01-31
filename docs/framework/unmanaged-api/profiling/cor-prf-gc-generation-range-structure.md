---
title: COR_PRF_GC_GENERATION_RANGE – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867203"
---
# <a name="cor_prf_gc_generation_range-structure"></a>COR_PRF_GC_GENERATION_RANGE – struktura
Popisuje rozsah (tj. blok) paměti, která přechází do uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`generation`|Hodnota výčtu [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , která určuje generaci, do které patří blok paměti.|  
|`rangeStart`|IDENTIFIKÁTOR objektu, který určuje počáteční umístění bloku paměti.|  
|`rangeLength`|Ukazatel na celé číslo, které určuje velikost použité části bloku paměti (tj. množství paměti využité v rámci bloku).|  
|`rangeLengthReserved`|Ukazatel na celé číslo, které určuje velikost bloku paměti (tj. velikost paměti rezervované pro blok).|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `rangeLength` je zaručena jako přesnost pouze v případě, že je [ICorProfilerInfo2:: GetGenerationBounds –](icorprofilerinfo2-getgenerationbounds-method.md) nebo [ICorProfilerInfo2:: GetObjectGeneration –](icorprofilerinfo2-getobjectgeneration-method.md), obě, které používají strukturu `COR_PRF_GC_GENERATION_RANGE`, volány z metody [ICorProfilerCallback2:: GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md) nebo [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](profiling-structures.md)
