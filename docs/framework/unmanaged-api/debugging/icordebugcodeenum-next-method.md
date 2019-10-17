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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac3fc157543f2990c7c9f9917140b35f8948108e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395479"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="08d2a-102">ICorDebugCodeEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="08d2a-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="08d2a-103">Získá zadaný počet instancí "ICorDebugCode" z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="08d2a-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="08d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08d2a-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="08d2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="08d2a-105">Parameters</span></span>

`celt`  
<span data-ttu-id="08d2a-106">pro Počet instancí `ICorDebugCode`, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="08d2a-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="08d2a-107">mimo Pole ukazatelů, z nichž každý odkazuje na objekt @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="08d2a-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="08d2a-108">mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="08d2a-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="08d2a-109">Tato hodnota může být null, pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="08d2a-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="08d2a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="08d2a-110">Requirements</span></span>

<span data-ttu-id="08d2a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d2a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="08d2a-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08d2a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="08d2a-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="08d2a-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="08d2a-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
