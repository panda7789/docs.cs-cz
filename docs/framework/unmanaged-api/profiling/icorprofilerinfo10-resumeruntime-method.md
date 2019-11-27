---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 515b42d649f68345f9924f57a91d146556480e0a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449798"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="85c37-102">ICorProfilerInfo10:: ResumeRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="85c37-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="85c37-103">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="85c37-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="85c37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85c37-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="85c37-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85c37-105">Requirements</span></span>

<span data-ttu-id="85c37-106">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="85c37-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="85c37-107">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="85c37-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="85c37-108">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85c37-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="85c37-109">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85c37-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="85c37-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85c37-110">See also</span></span>

- [<span data-ttu-id="85c37-111">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="85c37-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
