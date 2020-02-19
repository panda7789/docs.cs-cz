---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452172"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="12aa1-102">ICorProfilerInfo10:: RequestReJITWithInliners – metoda</span><span class="sxs-lookup"><span data-stu-id="12aa1-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="12aa1-103">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="12aa1-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="12aa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12aa1-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="12aa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12aa1-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="12aa1-106">\[in] Bitová maska [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="12aa1-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="12aa1-107">\[v] počet funkcí, které mají být rekompilovány.</span><span class="sxs-lookup"><span data-stu-id="12aa1-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="12aa1-108">\[in] Určuje `moduleId` část párů (`module`, `methodDef`), které identifikují funkce, které se mají znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="12aa1-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="12aa1-109">\[in] Určuje `methodId` část párů (`module`, `methodDef`), které identifikují funkce, které se mají znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="12aa1-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="12aa1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12aa1-110">Remarks</span></span>

<span data-ttu-id="12aa1-111">[RequestReJIT –](icorprofilerinfo4-requestrejit-method.md) neprovádí žádné sledování s vloženými metodami.</span><span class="sxs-lookup"><span data-stu-id="12aa1-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="12aa1-112">Bylo očekáváno, že Profiler buď zablokuje vkládání, nebo sleduje vkládání a `RequestReJIT` volání pro všechny zaregistrované, aby se zajistilo, že každá instance metody inlineed byla ReJITted.</span><span class="sxs-lookup"><span data-stu-id="12aa1-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="12aa1-113">To představuje problém s ReJIT při připojení, protože Profiler není k dispozici pro monitorování vkládání.</span><span class="sxs-lookup"><span data-stu-id="12aa1-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="12aa1-114">Tuto metodu lze volat, aby bylo zaručeno, že celá sada linií ReJITted bude také.</span><span class="sxs-lookup"><span data-stu-id="12aa1-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="12aa1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12aa1-115">Requirements</span></span>

<span data-ttu-id="12aa1-116">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="12aa1-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="12aa1-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="12aa1-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="12aa1-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12aa1-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="12aa1-119">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12aa1-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="12aa1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="12aa1-120">See also</span></span>

- [<span data-ttu-id="12aa1-121">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="12aa1-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
