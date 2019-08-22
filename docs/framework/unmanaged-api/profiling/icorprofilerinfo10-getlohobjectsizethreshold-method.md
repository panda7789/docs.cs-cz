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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661241"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="cb5ad-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold – metoda</span><span class="sxs-lookup"><span data-stu-id="cb5ad-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="cb5ad-103">Získá hodnotu nakonfigurované prahové hodnoty haldy velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="cb5ad-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="cb5ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb5ad-104">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a><span data-ttu-id="cb5ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb5ad-105">Parameters</span></span>

`pThreshold` \
<span data-ttu-id="cb5ad-106">mimo Prahová hodnota haldy pro velké objekty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="cb5ad-106">[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb5ad-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb5ad-107">Remarks</span></span>

<span data-ttu-id="cb5ad-108">Objekty větší než prahová hodnota haldy pro velké objekty budou přiděleny na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="cb5ad-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="cb5ad-109">Počínaje rozhraním .NET Core 3,0 je prahová hodnota haldy pro velké `pThreshold` objekty konfigurovatelná, bude obsahovat aktivní mezní velikost haldy pro velké objekty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="cb5ad-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb5ad-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb5ad-110">Requirements</span></span>

<span data-ttu-id="cb5ad-111">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="cb5ad-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="cb5ad-112">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb5ad-112">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="cb5ad-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb5ad-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="cb5ad-114">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5ad-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cb5ad-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb5ad-115">See also</span></span>

- [<span data-ttu-id="cb5ad-116">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="cb5ad-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
