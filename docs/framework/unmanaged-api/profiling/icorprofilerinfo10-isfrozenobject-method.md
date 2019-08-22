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
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661226"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="e1323-102">ICorProfilerInfo10:: IsFrozenObject – metoda</span><span class="sxs-lookup"><span data-stu-id="e1323-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="e1323-103">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e1323-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1323-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1323-104">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a><span data-ttu-id="e1323-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1323-105">Parameters</span></span>

`objectId` \
<span data-ttu-id="e1323-106">pro Objekt, který chcete prošetřit.</span><span class="sxs-lookup"><span data-stu-id="e1323-106">[in] The object to examine.</span></span>

`pbFrozen` \
<span data-ttu-id="e1323-107">mimo A `BOOL` označuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e1323-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="e1323-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1323-108">Requirements</span></span>

<span data-ttu-id="e1323-109">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="e1323-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="e1323-110">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1323-110">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e1323-111">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1323-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e1323-112">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1323-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e1323-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1323-113">See also</span></span>

- [<span data-ttu-id="e1323-114">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="e1323-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
