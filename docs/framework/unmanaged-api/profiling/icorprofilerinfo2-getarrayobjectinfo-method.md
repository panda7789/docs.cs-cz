---
title: ICorProfilerInfo2::GetArrayObjectInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 368b8f270797beb525e0745a29990667913f4071
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497349"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="4fefd-102">ICorProfilerInfo2::GetArrayObjectInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="4fefd-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="4fefd-103">Získá podrobné informace o objektu Array.</span><span class="sxs-lookup"><span data-stu-id="4fefd-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fefd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fefd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fefd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fefd-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="4fefd-106">pro ID platného objektu Array.</span><span class="sxs-lookup"><span data-stu-id="4fefd-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="4fefd-107">pro Pořadí (počet rozměrů) pole.</span><span class="sxs-lookup"><span data-stu-id="4fefd-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="4fefd-108">mimo Pole obsahující celá čísla, která představují velikost rozměru pole.</span><span class="sxs-lookup"><span data-stu-id="4fefd-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="4fefd-109">mimo Pole obsahující celá čísla, z nichž každá představuje dolní mez dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="4fefd-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="4fefd-110">mimo Ukazatel na adresu nezpracované vyrovnávací paměti pro pole, které je stanoveno podle konvence jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="4fefd-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fefd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fefd-111">Remarks</span></span>  
 <span data-ttu-id="4fefd-112">`pDimensionSizes`A `pDimensionLowerBounds` jsou paralelní pole, takže prvky nacházející se ve stejném indexu v každém poli jsou charakteristiky stejné entity.</span><span class="sxs-lookup"><span data-stu-id="4fefd-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fefd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fefd-113">Requirements</span></span>  
 <span data-ttu-id="4fefd-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fefd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fefd-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4fefd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fefd-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4fefd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fefd-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fefd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fefd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fefd-118">See also</span></span>

- [<span data-ttu-id="4fefd-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fefd-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4fefd-120">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fefd-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
