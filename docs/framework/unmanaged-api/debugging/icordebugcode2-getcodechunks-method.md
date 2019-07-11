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
ms.openlocfilehash: 4bbc7ac7d87c6a5d36dc3432c603bb7d16d62c00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747423"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="78709-102">ICorDebugCode2::GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="78709-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="78709-103">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="78709-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78709-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78709-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78709-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78709-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="78709-106">[in] Velikost `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="78709-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="78709-107">[out] Počet bloků, které jsou vráceny v `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="78709-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="78709-108">[out] Pole struktur "codechunkinfo –", z nichž každý představuje jediný neodkazovaný blok kódu.</span><span class="sxs-lookup"><span data-stu-id="78709-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="78709-109">Pokud hodnota `cbufSize` je 0, tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="78709-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78709-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78709-110">Remarks</span></span>  
 <span data-ttu-id="78709-111">Bloky kódu nikdy se překrývají a jejich brzo bude následovat pořadí, ve kterém jsou by mít byla zřetězených podle [icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="78709-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="78709-112">Objekt Microsoft intermediate language (MSIL) kódu v rozhraní .NET Framework verze 2.0 bude tvořit jeden blok.</span><span class="sxs-lookup"><span data-stu-id="78709-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78709-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78709-113">Requirements</span></span>  
 <span data-ttu-id="78709-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78709-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78709-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78709-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78709-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78709-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78709-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78709-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78709-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78709-118">See also</span></span>
