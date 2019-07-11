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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e18097dd380ee354e5652886544d40da074f1230
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747621"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="d20c7-102">ICorDebugCode::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="d20c7-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="d20c7-103">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="d20c7-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="d20c7-104">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d20c7-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d20c7-105">Použití [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="d20c7-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d20c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d20c7-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d20c7-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d20c7-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="d20c7-108">[in] Posun zahájení funkce.</span><span class="sxs-lookup"><span data-stu-id="d20c7-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="d20c7-109">[in] Posun od konce funkce.</span><span class="sxs-lookup"><span data-stu-id="d20c7-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="d20c7-110">[in] Velikost `buffer` pole, do které bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="d20c7-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d20c7-111">[out] Pole, do kterého bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="d20c7-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="d20c7-112">[out] Počet bajtů vrácených.</span><span class="sxs-lookup"><span data-stu-id="d20c7-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d20c7-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d20c7-113">Remarks</span></span>  
 <span data-ttu-id="d20c7-114">Pokud funkce kód byl rozdělen do více bloků dat, jsou spojeny v pořadí podle zvýšení nativní posun.</span><span class="sxs-lookup"><span data-stu-id="d20c7-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="d20c7-115">Instrukce hranice nekontrolují.</span><span class="sxs-lookup"><span data-stu-id="d20c7-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d20c7-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d20c7-116">Requirements</span></span>  
 <span data-ttu-id="d20c7-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d20c7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d20c7-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d20c7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d20c7-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d20c7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d20c7-120">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="d20c7-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20c7-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d20c7-121">See also</span></span>

- [<span data-ttu-id="d20c7-122">GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="d20c7-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
