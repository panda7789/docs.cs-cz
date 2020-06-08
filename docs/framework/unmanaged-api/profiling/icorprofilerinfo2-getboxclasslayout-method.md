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
ms.openlocfilehash: 630b67a64716f26577bbc376970e4f76216f4da5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497348"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="e23aa-102">ICorProfilerInfo2::GetBoxClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="e23aa-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="e23aa-103">Získá informace o tom, kde je zadaný typ hodnoty umístěný, když je zabalený.</span><span class="sxs-lookup"><span data-stu-id="e23aa-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e23aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e23aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e23aa-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e23aa-106">pro ID třídy, která popisuje typ hodnoty, která je zabalena.</span><span class="sxs-lookup"><span data-stu-id="e23aa-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e23aa-107">mimo Celé číslo, které je posunutí vzhledem k zabalenému ukazateli ID objektu typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e23aa-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e23aa-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e23aa-108">Remarks</span></span>  
 <span data-ttu-id="e23aa-109">`pBufferOffset`Hodnota je umístění typu hodnoty v rámci pole.</span><span class="sxs-lookup"><span data-stu-id="e23aa-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="e23aa-110">Po `pBufferOffset` použití na zabalený objekt lze použít rozložení třídy typu hodnoty pro interpretaci hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="e23aa-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23aa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e23aa-111">Requirements</span></span>  
 <span data-ttu-id="e23aa-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e23aa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23aa-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e23aa-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e23aa-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e23aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e23aa-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23aa-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e23aa-116">See also</span></span>

- [<span data-ttu-id="e23aa-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23aa-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e23aa-118">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23aa-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
