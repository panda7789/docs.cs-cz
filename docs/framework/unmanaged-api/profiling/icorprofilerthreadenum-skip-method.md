---
title: ICorProfilerThreadEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
ms.openlocfilehash: aaa8eaa2c4eb927a817425611f71e51c9f3d37af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447576"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="e03bb-102">ICorProfilerThreadEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="e03bb-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="e03bb-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span><span class="sxs-lookup"><span data-stu-id="e03bb-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e03bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e03bb-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e03bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e03bb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e03bb-106">[in] The number of elements to be skipped.</span><span class="sxs-lookup"><span data-stu-id="e03bb-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e03bb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e03bb-107">Return Value</span></span>  
 <span data-ttu-id="e03bb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span><span class="sxs-lookup"><span data-stu-id="e03bb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e03bb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e03bb-109">HRESULT</span></span>|<span data-ttu-id="e03bb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e03bb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e03bb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e03bb-111">S_OK</span></span>|<span data-ttu-id="e03bb-112">`celt` elements were skipped.</span><span class="sxs-lookup"><span data-stu-id="e03bb-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="e03bb-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e03bb-113">S_FALSE</span></span>|<span data-ttu-id="e03bb-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span><span class="sxs-lookup"><span data-stu-id="e03bb-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e03bb-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e03bb-115">Remarks</span></span>  
 <span data-ttu-id="e03bb-116">The new position of this enumerator's cursor is (current position) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="e03bb-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e03bb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e03bb-117">Requirements</span></span>  
 <span data-ttu-id="e03bb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e03bb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e03bb-119">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e03bb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e03bb-120">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e03bb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e03bb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e03bb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e03bb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e03bb-122">See also</span></span>

- [<span data-ttu-id="e03bb-123">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e03bb-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e03bb-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e03bb-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
