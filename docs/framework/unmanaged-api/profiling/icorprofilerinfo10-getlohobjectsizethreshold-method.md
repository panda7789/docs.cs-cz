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
ms.openlocfilehash: 7a0f6f6bea5bc919ebfe9c9acc3b02a31eaa7cd0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452211"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="8d9b7-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold – metoda</span><span class="sxs-lookup"><span data-stu-id="8d9b7-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="8d9b7-103">Získá hodnotu nakonfigurované prahové hodnoty haldy velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="8d9b7-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d9b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d9b7-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="8d9b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d9b7-105">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="8d9b7-106">\[] prahová hodnota haldy pro velké objekty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="8d9b7-106">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d9b7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d9b7-107">Remarks</span></span>

<span data-ttu-id="8d9b7-108">Objekty větší než prahová hodnota haldy pro velké objekty budou přiděleny na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="8d9b7-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="8d9b7-109">Počínaje rozhraním .NET Core 3,0 je prahová hodnota haldy velkých objektů konfigurovatelná, `pThreshold` bude obsahovat aktivní mezní velikost haldy velkých objektů v bajtech.</span><span class="sxs-lookup"><span data-stu-id="8d9b7-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d9b7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d9b7-110">Requirements</span></span>

<span data-ttu-id="8d9b7-111">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="8d9b7-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="8d9b7-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d9b7-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="8d9b7-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d9b7-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="8d9b7-114">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d9b7-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="8d9b7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d9b7-115">See also</span></span>

- [<span data-ttu-id="8d9b7-116">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="8d9b7-116">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
