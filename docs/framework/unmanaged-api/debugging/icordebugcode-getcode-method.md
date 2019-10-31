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
ms.openlocfilehash: db24228de7e8c98fd97f890b1e408515172299b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125674"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="fc6e1-102">ICorDebugCode::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="fc6e1-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="fc6e1-103">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="fc6e1-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fc6e1-105">Místo toho použijte [ICorDebugCode2:: getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc6e1-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6e1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc6e1-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fc6e1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc6e1-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="fc6e1-108">pro Posun začátku funkce</span><span class="sxs-lookup"><span data-stu-id="fc6e1-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="fc6e1-109">pro Posun konce funkce</span><span class="sxs-lookup"><span data-stu-id="fc6e1-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="fc6e1-110">pro Velikost pole `buffer`, do něhož bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="fc6e1-111">mimo Pole, do kterého bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="fc6e1-112">mimo Počet vrácených bajtů</span><span class="sxs-lookup"><span data-stu-id="fc6e1-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc6e1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc6e1-113">Remarks</span></span>  
 <span data-ttu-id="fc6e1-114">Pokud byl kód funkce rozdělen do více bloků dat, jsou zřetězeny v pořadí, ve kterém se zvyšuje nativní posun.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="fc6e1-115">Nekontrolují se hranice instrukcí.</span><span class="sxs-lookup"><span data-stu-id="fc6e1-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6e1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc6e1-116">Requirements</span></span>  
 <span data-ttu-id="fc6e1-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc6e1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6e1-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc6e1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc6e1-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fc6e1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc6e1-120">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="fc6e1-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc6e1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc6e1-121">See also</span></span>

- [<span data-ttu-id="fc6e1-122">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="fc6e1-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
