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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6e6f4f6bdfba8deecb3661d88a881759da043ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456304"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="2b913-102">ICorProfilerInfo2::GetArrayObjectInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="2b913-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="2b913-103">Získá podrobné informace o objektu array.</span><span class="sxs-lookup"><span data-stu-id="2b913-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b913-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b913-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b913-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b913-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="2b913-106">[v] ID objektu platné pole.</span><span class="sxs-lookup"><span data-stu-id="2b913-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="2b913-107">[v] Pořadí (počet dimenzí) pole.</span><span class="sxs-lookup"><span data-stu-id="2b913-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="2b913-108">[out] Pole, které obsahuje celá čísla, každý představuje velikost dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="2b913-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="2b913-109">[out] Pole obsahující celá čísla, každý představuje dolní hranice elementu dimenze pole.</span><span class="sxs-lookup"><span data-stu-id="2b913-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="2b913-110">[out] Ukazatel na adresu nezpracovaná vyrovnávací paměti pro pole, které je rozložená podle konvence C++.</span><span class="sxs-lookup"><span data-stu-id="2b913-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b913-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b913-111">Remarks</span></span>  
 <span data-ttu-id="2b913-112">`pDimensionSizes` a `pDimensionLowerBounds` jsou paralelní pole, takže prvky umístěné ve stejném indexu v každém poli jsou charakteristické vlastnosti třídy na stejnou entitu.</span><span class="sxs-lookup"><span data-stu-id="2b913-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b913-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b913-113">Requirements</span></span>  
 <span data-ttu-id="2b913-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b913-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b913-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b913-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b913-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b913-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b913-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b913-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b913-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b913-118">See Also</span></span>  
 [<span data-ttu-id="2b913-119">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b913-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2b913-120">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b913-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
