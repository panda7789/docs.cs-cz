---
title: ICorDebugCodeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125530"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="c87e2-102">ICorDebugCodeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c87e2-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="c87e2-103">Získá zadaný počet instancí "ICorDebugCode" z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="c87e2-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="c87e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c87e2-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="c87e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c87e2-105">Parameters</span></span>

`celt`  
<span data-ttu-id="c87e2-106">pro Počet instancí `ICorDebugCode`, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="c87e2-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="c87e2-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="c87e2-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="c87e2-108">mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="c87e2-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="c87e2-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="c87e2-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="c87e2-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c87e2-110">Requirements</span></span>

<span data-ttu-id="c87e2-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c87e2-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c87e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="c87e2-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c87e2-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c87e2-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
