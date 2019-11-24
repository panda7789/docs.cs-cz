---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7a38ee4ae74ca5b96dd082e752fc733eb85fca3f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427018"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="8bb6c-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span><span class="sxs-lookup"><span data-stu-id="8bb6c-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="8bb6c-103">Gets the value of the configured large object heap (LOH) threshold.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="8bb6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bb6c-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a><span data-ttu-id="8bb6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb6c-105">Parameters</span></span>

`pThreshold` \
<span data-ttu-id="8bb6c-106">[out] The large object heap threshold in bytes.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-106">[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="8bb6c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bb6c-107">Remarks</span></span>

<span data-ttu-id="8bb6c-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="8bb6c-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span><span class="sxs-lookup"><span data-stu-id="8bb6c-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="8bb6c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bb6c-110">Requirements</span></span>

<span data-ttu-id="8bb6c-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="8bb6c-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="8bb6c-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bb6c-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="8bb6c-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bb6c-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8bb6c-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bb6c-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8bb6c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bb6c-115">See also</span></span>

- [<span data-ttu-id="8bb6c-116">ICorProfilerInfo10 Interface</span><span class="sxs-lookup"><span data-stu-id="8bb6c-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
