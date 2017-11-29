---
title: "ICorDebugCode::GetCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12820d0be725c92754640aaa4eebca56bbc33ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="07b9b-102">ICorDebugCode::GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="07b9b-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="07b9b-103">Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad.</span><span class="sxs-lookup"><span data-stu-id="07b9b-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="07b9b-104">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="07b9b-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="07b9b-105">Použití [icordebugcode2::getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="07b9b-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07b9b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07b9b-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07b9b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="07b9b-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="07b9b-108">[v] Posun od funkce.</span><span class="sxs-lookup"><span data-stu-id="07b9b-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="07b9b-109">[v] Posun konec funkce.</span><span class="sxs-lookup"><span data-stu-id="07b9b-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="07b9b-110">[v] Velikost `buffer` pole, do které bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="07b9b-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="07b9b-111">[out] Pole, do kterého bude vrácen kód.</span><span class="sxs-lookup"><span data-stu-id="07b9b-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="07b9b-112">[out] Počet bajtů vrácených.</span><span class="sxs-lookup"><span data-stu-id="07b9b-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07b9b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07b9b-113">Remarks</span></span>  
 <span data-ttu-id="07b9b-114">Pokud kód funkce byl rozdělen do více bloků dat, jsou zřetězeny v pořadí podle zvýšení nativní posun.</span><span class="sxs-lookup"><span data-stu-id="07b9b-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="07b9b-115">Instrukce hranice nejsou zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="07b9b-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07b9b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="07b9b-116">Requirements</span></span>  
 <span data-ttu-id="07b9b-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07b9b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07b9b-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07b9b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07b9b-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07b9b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07b9b-120">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="07b9b-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b9b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="07b9b-121">See Also</span></span>  
 [<span data-ttu-id="07b9b-122">Getcodechunks – metoda</span><span class="sxs-lookup"><span data-stu-id="07b9b-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
