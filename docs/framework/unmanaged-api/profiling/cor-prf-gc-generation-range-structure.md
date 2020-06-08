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
ms.openlocfilehash: 91fb902aab678e29c6e74380e3576fa5c4ae62d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500888"
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
  
|Člen|Description|  
|------------|-----------------|  
|`generation`|Hodnota výčtu [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , která určuje generaci, do které patří blok paměti.|  
|`rangeStart`|IDENTIFIKÁTOR objektu, který určuje počáteční umístění bloku paměti.|  
|`rangeLength`|Ukazatel na celé číslo, které určuje velikost použité části bloku paměti (tj. množství paměti využité v rámci bloku).|  
|`rangeLengthReserved`|Ukazatel na celé číslo, které určuje velikost bloku paměti (tj. velikost paměti rezervované pro blok).|  
  
## <a name="remarks"></a>Poznámky  
 `rangeLength`Hodnota je zaručena jako přesnost pouze v případě, že [ICorProfilerInfo2:: GetGenerationBounds –](icorprofilerinfo2-getgenerationbounds-method.md) nebo [ICorProfilerInfo2:: GetObjectGeneration –](icorprofilerinfo2-getobjectgeneration-method.md), oba, které používají `COR_PRF_GC_GENERATION_RANGE` strukturu, je volána z metody [ICorProfilerCallback2:: GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md) nebo [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](profiling-structures.md)
