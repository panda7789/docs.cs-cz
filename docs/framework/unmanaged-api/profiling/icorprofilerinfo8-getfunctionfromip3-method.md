---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868327"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="6f8db-102">ICorProfilerInfo8:: GetFunctionFromIP3 – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8db-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="6f8db-103">Mapuje ukazatel na instrukci spravovaného kódu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="6f8db-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="6f8db-104">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="6f8db-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f8db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f8db-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="6f8db-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f8db-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="6f8db-107">\[in] ukazatel na instrukci ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="6f8db-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="6f8db-108">\[] ID funkce.</span><span class="sxs-lookup"><span data-stu-id="6f8db-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="6f8db-109">\[] identita funkce Rekompilované JIT.</span><span class="sxs-lookup"><span data-stu-id="6f8db-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f8db-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f8db-110">Remarks</span></span>

<span data-ttu-id="6f8db-111">Tato metoda spolupracuje s dynamickými i nedynamickými metodami.</span><span class="sxs-lookup"><span data-stu-id="6f8db-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="6f8db-112">Je nadmnožinou [getfunctionfromip2 –](icorprofilerinfo4-getfunctionfromip2-method.md), která funguje pouze pro funkce s metadaty.</span><span class="sxs-lookup"><span data-stu-id="6f8db-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f8db-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f8db-113">Requirements</span></span>

<span data-ttu-id="6f8db-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f8db-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6f8db-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6f8db-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="6f8db-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6f8db-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6f8db-117">**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6f8db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6f8db-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f8db-118">See also</span></span>

- [<span data-ttu-id="6f8db-119">Rozhraní ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="6f8db-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
