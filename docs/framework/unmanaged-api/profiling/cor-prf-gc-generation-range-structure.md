---
title: "COR_PRF_GC_GENERATION_RANGE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION_RANGE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords: COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59969f45d4cca0ff208bd9e77c93994cad61ab13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="8c6ef-102">COR_PRF_GC_GENERATION_RANGE – struktura</span><span class="sxs-lookup"><span data-stu-id="8c6ef-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="8c6ef-103">Popisuje rozsah (blok) paměti, která probíhá uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6ef-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="8c6ef-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8c6ef-105">Members</span></span>  
  
|<span data-ttu-id="8c6ef-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8c6ef-106">Member</span></span>|<span data-ttu-id="8c6ef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8c6ef-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="8c6ef-108">Hodnota [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčet, který určuje bloku paměti generace, ke kterému patří.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="8c6ef-109">ID objektu, který určuje výchozí umístění bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="8c6ef-110">Ukazatel na celé číslo, které určuje velikost používané část bloku paměti (který je množství paměti v rámci bloku).</span><span class="sxs-lookup"><span data-stu-id="8c6ef-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="8c6ef-111">Ukazatel na celé číslo, které určuje velikost bloku paměti (to znamená, množství paměti vyhrazené pro blok).</span><span class="sxs-lookup"><span data-stu-id="8c6ef-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c6ef-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c6ef-112">Remarks</span></span>  
 <span data-ttu-id="8c6ef-113">`rangeLength` Hodnota představuje záruku přesné pouze v případě [ICorProfilerInfo2::getgenerationbounds –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) nebo [ICorProfilerInfo2::getobjectgeneration –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), obě kteří používají `COR_PRF_GC_GENERATION_RANGE` struktury, je volána z [icorprofilercallback2::garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) nebo [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c6ef-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c6ef-114">Requirements</span></span>  
 <span data-ttu-id="8c6ef-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c6ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c6ef-116">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="8c6ef-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8c6ef-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c6ef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c6ef-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c6ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c6ef-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c6ef-119">See Also</span></span>  
 [<span data-ttu-id="8c6ef-120">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8c6ef-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
