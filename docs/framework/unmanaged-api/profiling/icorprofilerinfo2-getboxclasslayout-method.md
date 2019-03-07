---
title: ICorProfilerInfo2::GetBoxClassLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2943a70f563b82d3578ed7fbd98b981282a1dd5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472600"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="c657a-102">ICorProfilerInfo2::GetBoxClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="c657a-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="c657a-103">Získá informace o tom, kde je zadanou hodnotu typu umístěn při je zabalená.</span><span class="sxs-lookup"><span data-stu-id="c657a-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c657a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c657a-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c657a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c657a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="c657a-106">[in] ID třídy, která popisuje typ hodnoty, který je v poli.</span><span class="sxs-lookup"><span data-stu-id="c657a-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="c657a-107">[out] Celé číslo, které je posun vzhledem k ukazatel ID zabalený objekt typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c657a-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c657a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c657a-108">Remarks</span></span>  
 <span data-ttu-id="c657a-109">`pBufferOffset` Hodnota označuje umístění systému typ hodnoty v poli.</span><span class="sxs-lookup"><span data-stu-id="c657a-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="c657a-110">Po `pBufferOffset` se použije na zabalený objekt rozložení třídy typ hodnoty je možné pro interpretaci hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="c657a-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c657a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c657a-111">Requirements</span></span>  
 <span data-ttu-id="c657a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c657a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c657a-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c657a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c657a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c657a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c657a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c657a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c657a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c657a-116">See also</span></span>
- [<span data-ttu-id="c657a-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c657a-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c657a-118">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c657a-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
