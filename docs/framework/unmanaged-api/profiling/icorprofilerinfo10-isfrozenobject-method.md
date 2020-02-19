---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 21f9cb415f913a9c865a487f6e80523344db811e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452185"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="f5108-102">ICorProfilerInfo10:: IsFrozenObject – metoda</span><span class="sxs-lookup"><span data-stu-id="f5108-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="f5108-103">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f5108-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5108-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5108-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="f5108-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5108-105">Parameters</span></span>

- `objectId`

  <span data-ttu-id="f5108-106">\[v] objektu, který chcete prošetřit.</span><span class="sxs-lookup"><span data-stu-id="f5108-106">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="f5108-107">\[] `BOOL` označující, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f5108-107">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5108-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5108-108">Requirements</span></span>

<span data-ttu-id="f5108-109">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f5108-109">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="f5108-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f5108-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f5108-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5108-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f5108-112">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5108-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f5108-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5108-113">See also</span></span>

- [<span data-ttu-id="f5108-114">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="f5108-114">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
