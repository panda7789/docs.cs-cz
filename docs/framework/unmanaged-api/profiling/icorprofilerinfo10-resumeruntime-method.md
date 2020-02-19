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
ms.openlocfilehash: a3dca2cbb138dbc43f477488032e67335c8b15f9
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452159"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="da920-102">ICorProfilerInfo10:: ResumeRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="da920-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="da920-103">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="da920-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="da920-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da920-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="da920-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da920-105">Requirements</span></span>

<span data-ttu-id="da920-106">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="da920-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="da920-107">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="da920-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="da920-108">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="da920-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="da920-109">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da920-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="da920-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="da920-110">See also</span></span>

- [<span data-ttu-id="da920-111">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="da920-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
