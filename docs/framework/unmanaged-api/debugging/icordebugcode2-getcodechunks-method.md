---
title: "ICorDebugCode2::GetCodeChunks – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b90913f05cc2e0a3e98a5890f76a41eb2eafc6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="dc49f-102">ICorDebugCode2::GetCodeChunks – metoda</span><span class="sxs-lookup"><span data-stu-id="dc49f-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="dc49f-103">Získá bloky kódu, ze kterých je tento objekt kódu sestaven.</span><span class="sxs-lookup"><span data-stu-id="dc49f-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc49f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc49f-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc49f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc49f-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="dc49f-106">[v] Velikost `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="dc49f-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="dc49f-107">[out] Číslo, vrátí se v bloků dat `chunks` pole.</span><span class="sxs-lookup"><span data-stu-id="dc49f-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="dc49f-108">[out] Pole "Codechunkinfo –" struktury, z nichž každý představuje jeden blok kódu.</span><span class="sxs-lookup"><span data-stu-id="dc49f-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="dc49f-109">Pokud hodnota `cbufSize` je 0, tento parametr může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dc49f-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc49f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc49f-110">Remarks</span></span>  
 <span data-ttu-id="dc49f-111">Bloky kódu se nikdy překrývají a jejich bude postupovat podle pořadí, ve kterém se by mít byla zřetězených podle [icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc49f-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="dc49f-112">Objekt Microsoft (MSIL intermediate language) kódu v rozhraní .NET Framework verze 2.0 bude tvoří jeden kód bloku.</span><span class="sxs-lookup"><span data-stu-id="dc49f-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc49f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc49f-113">Requirements</span></span>  
 <span data-ttu-id="dc49f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc49f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc49f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc49f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc49f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc49f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc49f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc49f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc49f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc49f-118">See Also</span></span>  
 
