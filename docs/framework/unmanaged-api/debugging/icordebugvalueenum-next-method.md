---
title: "ICorDebugValueEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 71775db7134c8f376099b0820f4330602d3db0e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="f5b9d-102">ICorDebugValueEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f5b9d-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="f5b9d-103">Získá zadaný počet instancí "ICorDebugValue" z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="f5b9d-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5b9d-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5b9d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5b9d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f5b9d-106">[v] Počet `ICorDebugValue` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="f5b9d-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="f5b9d-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="f5b9d-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f5b9d-108">[out] Ukazatel na počet `ICorDebugValue` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="f5b9d-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="f5b9d-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="f5b9d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b9d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5b9d-110">Requirements</span></span>  
 <span data-ttu-id="f5b9d-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b9d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b9d-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5b9d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5b9d-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5b9d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5b9d-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b9d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5b9d-115">See Also</span></span>  
    
 
