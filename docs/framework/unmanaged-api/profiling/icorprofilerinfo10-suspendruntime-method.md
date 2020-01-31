---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: a4c875f6aae996271dee9ac193768ef6981efc19
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863033"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="321c8-102">ICorProfilerInfo10:: SuspendRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="321c8-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="321c8-103">Pozastaví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="321c8-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="321c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="321c8-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="321c8-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="321c8-105">Requirements</span></span>

<span data-ttu-id="321c8-106">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="321c8-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="321c8-107">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="321c8-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="321c8-108">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="321c8-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="321c8-109">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321c8-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="321c8-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="321c8-110">See also</span></span>

- [<span data-ttu-id="321c8-111">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="321c8-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
