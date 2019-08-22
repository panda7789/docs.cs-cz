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
ms.openlocfilehash: cf599e5ded73b09d54c98dcd99f51b30c6a4ba82
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661207"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="4a43d-102">ICorProfilerInfo10:: ResumeRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="4a43d-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="4a43d-103">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="4a43d-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a43d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a43d-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="4a43d-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a43d-105">Requirements</span></span>

<span data-ttu-id="4a43d-106">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="4a43d-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="4a43d-107">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a43d-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="4a43d-108">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a43d-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="4a43d-109">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a43d-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4a43d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a43d-110">See also</span></span>

- [<span data-ttu-id="4a43d-111">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="4a43d-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
