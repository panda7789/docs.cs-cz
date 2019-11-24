---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7593e8873c2714df85146903c0052a9909a95ccd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444712"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="f16b0-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span><span class="sxs-lookup"><span data-stu-id="f16b0-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="f16b0-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span><span class="sxs-lookup"><span data-stu-id="f16b0-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="f16b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f16b0-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a><span data-ttu-id="f16b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f16b0-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="f16b0-106">[in] The ID of the function whose native code start addresses should be returned.</span><span class="sxs-lookup"><span data-stu-id="f16b0-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>

`reJitId` \
<span data-ttu-id="f16b0-107">[in] The identity of the JIT-recompiled function.</span><span class="sxs-lookup"><span data-stu-id="f16b0-107">[in] The identity of the JIT-recompiled function.</span></span>

`cCodeStartAddresses` \
<span data-ttu-id="f16b0-108">[in] The maximum size of the `codeStartAddresses` array.</span><span class="sxs-lookup"><span data-stu-id="f16b0-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

`pcCodeStartAddresses` \
<span data-ttu-id="f16b0-109">[out] The number of available addresses.</span><span class="sxs-lookup"><span data-stu-id="f16b0-109">[out] The number of available addresses.</span></span>

`codeStartAddresses` \
<span data-ttu-id="f16b0-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span><span class="sxs-lookup"><span data-stu-id="f16b0-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="f16b0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f16b0-111">Remarks</span></span>

<span data-ttu-id="f16b0-112">When tiered compilation is enabled, a function may have more than one native code body.</span><span class="sxs-lookup"><span data-stu-id="f16b0-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="f16b0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f16b0-113">Requirements</span></span>

<span data-ttu-id="f16b0-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f16b0-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="f16b0-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f16b0-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f16b0-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f16b0-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f16b0-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f16b0-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f16b0-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f16b0-118">See also</span></span>

- [<span data-ttu-id="f16b0-119">ICorProfilerInfo9 Interface</span><span class="sxs-lookup"><span data-stu-id="f16b0-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
