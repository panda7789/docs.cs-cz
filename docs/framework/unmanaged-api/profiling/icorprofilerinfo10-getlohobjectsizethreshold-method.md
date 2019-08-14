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
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973753"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="4f8f0-102">ICorProfilerInfo10:: GetLOHObjectSizeThreshold – metoda</span><span class="sxs-lookup"><span data-stu-id="4f8f0-102">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>
  
 <span data-ttu-id="4f8f0-103">Získá hodnotu nakonfigurované prahové hodnoty haldy velkého objektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="4f8f0-103">Gets the value of the configured large object heap (LOH) threshold.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="4f8f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f8f0-104">Syntax</span></span>  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f8f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f8f0-105">Parameters</span></span>  
 `pThreshold` \
 <span data-ttu-id="4f8f0-106">mimo Prahová hodnota haldy pro velké objekty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-106">[out] The large object heap threshold in bytes.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="4f8f0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f8f0-107">Remarks</span></span>  
 <span data-ttu-id="4f8f0-108">Objekty větší než prahová hodnota haldy pro velké objekty budou přiděleny na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-108">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="4f8f0-109">Počínaje rozhraním .NET Core 3,0 je prahová hodnota haldy pro velké `pThreshold` objekty konfigurovatelná, bude obsahovat aktivní mezní velikost haldy pro velké objekty v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4f8f0-109">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="4f8f0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f8f0-110">Requirements</span></span>  
 <span data-ttu-id="4f8f0-111">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="4f8f0-111">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="4f8f0-112">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4f8f0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f8f0-113">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f8f0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f8f0-114">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f8f0-114">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4f8f0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f8f0-115">See also</span></span>
- [<span data-ttu-id="4f8f0-116">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="4f8f0-116">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

