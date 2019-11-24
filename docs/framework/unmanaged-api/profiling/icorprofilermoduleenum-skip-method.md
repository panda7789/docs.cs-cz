---
title: ICorProfilerModuleEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: d8c0f69ce407638aed6475c4d84d0e032cc6a8f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435988"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="c424b-102">ICorProfilerModuleEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="c424b-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="c424b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="c424b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c424b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c424b-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c424b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c424b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c424b-106">[in] The number of elements to be skipped.</span><span class="sxs-lookup"><span data-stu-id="c424b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c424b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c424b-107">Return Value</span></span>  
 <span data-ttu-id="c424b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span><span class="sxs-lookup"><span data-stu-id="c424b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c424b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c424b-109">HRESULT</span></span>|<span data-ttu-id="c424b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c424b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c424b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c424b-111">S_OK</span></span>|<span data-ttu-id="c424b-112">`celt` elements were skipped.</span><span class="sxs-lookup"><span data-stu-id="c424b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="c424b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c424b-113">S_FALSE</span></span>|<span data-ttu-id="c424b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span><span class="sxs-lookup"><span data-stu-id="c424b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c424b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c424b-115">Remarks</span></span>  
 <span data-ttu-id="c424b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="c424b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c424b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c424b-117">Requirements</span></span>  
 <span data-ttu-id="c424b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c424b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c424b-119">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c424b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c424b-120">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c424b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c424b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c424b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c424b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c424b-122">See also</span></span>

- [<span data-ttu-id="c424b-123">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c424b-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="c424b-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c424b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
