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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d64773aa0d35f2e97232576d145dfcba624812ec
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395533"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="687e2-102">ICorDebugCode2::GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="687e2-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="687e2-103">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="687e2-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="687e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="687e2-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="687e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="687e2-105">Parameters</span></span>

`cbufSize`  
<span data-ttu-id="687e2-106">pro Velikost pole `chunks`</span><span class="sxs-lookup"><span data-stu-id="687e2-106">[in] Size of the `chunks` array.</span></span>

`pcnumChunks`  
<span data-ttu-id="687e2-107">mimo Počet bloků vrácených v poli `chunks`</span><span class="sxs-lookup"><span data-stu-id="687e2-107">[out] The number of chunks returned in the `chunks` array.</span></span>

`chunks`  
<span data-ttu-id="687e2-108">mimo Pole struktur "Codechunkinfo –", z nichž každý představuje jeden blok kódu.</span><span class="sxs-lookup"><span data-stu-id="687e2-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="687e2-109">Pokud je hodnota `cbufSize` 0, tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="687e2-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="687e2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="687e2-110">Remarks</span></span>

<span data-ttu-id="687e2-111">Bloky kódu se nikdy nepřekrývají a budou postupovat podle pořadí, ve kterém by byly zřetězeny pomocí [ICorDebugCode:: GetCode](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="687e2-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="687e2-112">Objekt kódu jazyka MSIL (Microsoft Intermediate Language) ve verzi .NET Framework 2,0 bude obsahovat jeden blok kódu.</span><span class="sxs-lookup"><span data-stu-id="687e2-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="687e2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="687e2-113">Requirements</span></span>

<span data-ttu-id="687e2-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="687e2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="687e2-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="687e2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="687e2-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="687e2-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="687e2-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="687e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
