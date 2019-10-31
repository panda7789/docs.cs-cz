---
title: ICorDebugCode2::GetCodeChunks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
ms.openlocfilehash: e419ebb6ffd404368baf32e591e08c4a70645127
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121112"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="68e70-102">ICorDebugCode2::GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="68e70-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="68e70-103">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="68e70-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="68e70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68e70-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="68e70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68e70-105">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="68e70-106">pro Velikost pole `chunks`</span><span class="sxs-lookup"><span data-stu-id="68e70-106">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="68e70-107">mimo Počet bloků vrácených v poli `chunks`.</span><span class="sxs-lookup"><span data-stu-id="68e70-107">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="68e70-108">mimo Pole struktur "Codechunkinfo –", z nichž každý představuje jeden blok kódu.</span><span class="sxs-lookup"><span data-stu-id="68e70-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="68e70-109">Pokud je hodnota `cbufSize` 0, tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="68e70-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="68e70-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68e70-110">Remarks</span></span>

<span data-ttu-id="68e70-111">Bloky kódu se nikdy nepřekrývají a budou postupovat podle pořadí, ve kterém by byly zřetězeny pomocí [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="68e70-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="68e70-112">Objekt kódu jazyka MSIL (Microsoft Intermediate Language) ve verzi .NET Framework 2,0 bude obsahovat jeden blok kódu.</span><span class="sxs-lookup"><span data-stu-id="68e70-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="68e70-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68e70-113">Requirements</span></span>

<span data-ttu-id="68e70-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68e70-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="68e70-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68e70-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="68e70-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="68e70-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="68e70-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e70-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
