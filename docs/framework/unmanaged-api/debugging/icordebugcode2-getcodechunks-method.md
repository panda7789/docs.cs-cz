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
ms.openlocfilehash: 1428fc245d4f6993050c2753321684afee488c0e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116778"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="6e806-102">ICorDebugCode2::GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="6e806-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="6e806-103">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="6e806-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e806-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e806-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e806-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e806-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="6e806-106">[in] Velikost `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="6e806-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="6e806-107">[out] Počet bloků, které jsou vráceny v `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="6e806-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="6e806-108">[out] Pole struktur "codechunkinfo –", z nichž každý představuje jediný neodkazovaný blok kódu.</span><span class="sxs-lookup"><span data-stu-id="6e806-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="6e806-109">Pokud hodnota `cbufSize` je 0, tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6e806-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e806-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e806-110">Remarks</span></span>  
 <span data-ttu-id="6e806-111">Bloky kódu nikdy se překrývají a jejich brzo bude následovat pořadí, ve kterém jsou by mít byla zřetězených podle [icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e806-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="6e806-112">Objekt Microsoft intermediate language (MSIL) kódu v rozhraní .NET Framework verze 2.0 bude tvořit jeden blok.</span><span class="sxs-lookup"><span data-stu-id="6e806-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e806-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e806-113">Requirements</span></span>  
 <span data-ttu-id="6e806-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e806-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e806-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e806-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e806-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e806-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e806-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e806-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e806-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e806-118">See also</span></span>
