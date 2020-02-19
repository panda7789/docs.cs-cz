---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 9aadf9701444d215291b6fc19cc8cd61ca832837
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452237"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="15fce-102">ICorProfilerInfo10:: EnumerateObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="15fce-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="15fce-103">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="15fce-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="15fce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15fce-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="15fce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15fce-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="15fce-106">\[v] objekt pro zobrazení výčtu odkazů.</span><span class="sxs-lookup"><span data-stu-id="15fce-106">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="15fce-107">\[v] funkce, která bude volána s odkazy pro objekt.</span><span class="sxs-lookup"><span data-stu-id="15fce-107">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="15fce-108">\[v] data poskytnutá profilerem, která se mají předat funkci `callback`.</span><span class="sxs-lookup"><span data-stu-id="15fce-108">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="15fce-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15fce-109">Remarks</span></span>

<span data-ttu-id="15fce-110">Metoda `EnumerateObjectReferences` je podobná [objectReferences –](icorprofilercallback-objectreferences-method.md), s tím rozdílem, že prochází odkazy na vyžádání pro Profiler místo předběžného přidělení pole pro uložení odkazů.</span><span class="sxs-lookup"><span data-stu-id="15fce-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="15fce-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15fce-111">Requirements</span></span>

<span data-ttu-id="15fce-112">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="15fce-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="15fce-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15fce-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="15fce-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15fce-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="15fce-115">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15fce-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="15fce-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="15fce-116">See also</span></span>

- [<span data-ttu-id="15fce-117">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="15fce-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
