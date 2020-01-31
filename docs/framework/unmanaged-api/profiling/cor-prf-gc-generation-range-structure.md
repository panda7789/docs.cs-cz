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
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="d09b7-102">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="d09b7-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="d09b7-103">Popisuje rozsah (tj. blok) paměti, která přechází do uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d09b7-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d09b7-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="d09b7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d09b7-105">Members</span></span>  
  
|<span data-ttu-id="d09b7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d09b7-106">Member</span></span>|<span data-ttu-id="d09b7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d09b7-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="d09b7-108">Hodnota výčtu [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , která určuje generaci, do které patří blok paměti.</span><span class="sxs-lookup"><span data-stu-id="d09b7-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="d09b7-109">IDENTIFIKÁTOR objektu, který určuje počáteční umístění bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="d09b7-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="d09b7-110">Ukazatel na celé číslo, které určuje velikost použité části bloku paměti (tj. množství paměti využité v rámci bloku).</span><span class="sxs-lookup"><span data-stu-id="d09b7-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="d09b7-111">Ukazatel na celé číslo, které určuje velikost bloku paměti (tj. velikost paměti rezervované pro blok).</span><span class="sxs-lookup"><span data-stu-id="d09b7-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d09b7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d09b7-112">Remarks</span></span>  
 <span data-ttu-id="d09b7-113">Hodnota `rangeLength` je zaručena jako přesnost pouze v případě, že je [ICorProfilerInfo2:: GetGenerationBounds –](icorprofilerinfo2-getgenerationbounds-method.md) nebo [ICorProfilerInfo2:: GetObjectGeneration –](icorprofilerinfo2-getobjectgeneration-method.md), obě, které používají strukturu `COR_PRF_GC_GENERATION_RANGE`, volány z metody [ICorProfilerCallback2:: GarbageCollectionStarted –](icorprofilercallback2-garbagecollectionstarted-method.md) nebo [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d09b7-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d09b7-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d09b7-114">Requirements</span></span>  
 <span data-ttu-id="d09b7-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09b7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09b7-116">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d09b7-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d09b7-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d09b7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d09b7-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09b7-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d09b7-119">See also</span></span>

- [<span data-ttu-id="d09b7-120">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d09b7-120">Profiling Structures</span></span>](profiling-structures.md)
