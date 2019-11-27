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
ms.openlocfilehash: d6518612c213d21c2dc7d80878121ccd3b7e2abb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449849"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="309b0-102">ICorProfilerInfo10:: EnumerateObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="309b0-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="309b0-103">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="309b0-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="309b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="309b0-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="309b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="309b0-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="309b0-106">pro Objekt, na kterém se mají vytvořit výčet odkazů</span><span class="sxs-lookup"><span data-stu-id="309b0-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="309b0-107">pro Funkce, která bude volána s odkazy pro objekt.</span><span class="sxs-lookup"><span data-stu-id="309b0-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="309b0-108">pro Data poskytnutá profilerem, která se mají předat funkci `callback`</span><span class="sxs-lookup"><span data-stu-id="309b0-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="309b0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="309b0-109">Remarks</span></span>

<span data-ttu-id="309b0-110">Metoda `EnumerateObjectReferences` je podobná [objectReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), s tím rozdílem, že prochází odkazy na vyžádání pro Profiler místo předběžného přidělení pole pro uložení odkazů.</span><span class="sxs-lookup"><span data-stu-id="309b0-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="309b0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="309b0-111">Requirements</span></span>

<span data-ttu-id="309b0-112">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="309b0-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="309b0-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="309b0-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="309b0-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="309b0-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="309b0-115">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309b0-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="309b0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="309b0-116">See also</span></span>

- [<span data-ttu-id="309b0-117">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="309b0-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
