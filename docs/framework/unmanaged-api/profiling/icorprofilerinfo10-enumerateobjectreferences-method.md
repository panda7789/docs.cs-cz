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
ms.openlocfilehash: ac193b6b78434245b8f11a4f627b4e1992feb8a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661274"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="14cec-102">ICorProfilerInfo10:: EnumerateObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="14cec-102">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="14cec-103">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="14cec-103">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="14cec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14cec-104">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a><span data-ttu-id="14cec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14cec-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="14cec-106">pro Objekt, na kterém se mají vytvořit výčet odkazů</span><span class="sxs-lookup"><span data-stu-id="14cec-106">[in] The object to enumerate references on.</span></span>

`callback` \
<span data-ttu-id="14cec-107">pro Funkce, která bude volána s odkazy pro objekt.</span><span class="sxs-lookup"><span data-stu-id="14cec-107">[in] The function that will be called with the references for the object.</span></span>

`clientData` \
<span data-ttu-id="14cec-108">pro Data poskytnutá profilerem, která se `callback` mají předat funkci</span><span class="sxs-lookup"><span data-stu-id="14cec-108">[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="14cec-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14cec-109">Remarks</span></span>

<span data-ttu-id="14cec-110">Metoda je podobná objectReferences –, s tím rozdílem, že prochází odkazy na vyžádání pro Profiler místo předběžného přidělení pole pro uložení odkazů. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) `EnumerateObjectReferences`</span><span class="sxs-lookup"><span data-stu-id="14cec-110">The `EnumerateObjectReferences` method is similar to [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="14cec-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14cec-111">Requirements</span></span>

<span data-ttu-id="14cec-112">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="14cec-112">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="14cec-113">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14cec-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="14cec-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14cec-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="14cec-115">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14cec-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="14cec-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14cec-116">See also</span></span>

- [<span data-ttu-id="14cec-117">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="14cec-117">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
