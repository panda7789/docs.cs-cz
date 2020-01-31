---
title: ICorDebugCode::GetCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: 14a72e4622aac09840e43f8bcdcf8a8c8d6e6892
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777919"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="c2cfc-102">ICorDebugCode::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="c2cfc-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="c2cfc-103">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="c2cfc-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c2cfc-105">Místo toho použijte [ICorDebugCode2:: getcodechunks –](icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c2cfc-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cfc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2cfc-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2cfc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2cfc-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="c2cfc-108">pro Posun začátku funkce</span><span class="sxs-lookup"><span data-stu-id="c2cfc-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="c2cfc-109">pro Posun konce funkce</span><span class="sxs-lookup"><span data-stu-id="c2cfc-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="c2cfc-110">pro Velikost pole `buffer`, do něhož bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c2cfc-111">mimo Pole, do kterého bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="c2cfc-112">mimo Počet vrácených bajtů</span><span class="sxs-lookup"><span data-stu-id="c2cfc-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2cfc-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2cfc-113">Remarks</span></span>  
 <span data-ttu-id="c2cfc-114">Pokud byl kód funkce rozdělen do více bloků dat, jsou zřetězeny v pořadí, ve kterém se zvyšuje nativní posun.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="c2cfc-115">Nekontrolují se hranice instrukcí.</span><span class="sxs-lookup"><span data-stu-id="c2cfc-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2cfc-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2cfc-116">Requirements</span></span>  
 <span data-ttu-id="c2cfc-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2cfc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2cfc-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2cfc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2cfc-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2cfc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2cfc-120">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c2cfc-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cfc-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2cfc-121">See also</span></span>

- [<span data-ttu-id="c2cfc-122">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="c2cfc-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
