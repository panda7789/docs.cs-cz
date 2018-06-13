---
title: ICorDebugValueEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 433e387365834498203e444ed2f85889f8adde06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420441"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="df4d5-102">ICorDebugValueEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="df4d5-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="df4d5-103">Získá zadaný počet instancí "ICorDebugValue" z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="df4d5-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df4d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df4d5-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df4d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df4d5-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="df4d5-106">[v] Počet `ICorDebugValue` instancí, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="df4d5-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="df4d5-107">[out] Ukazatele, každý z nich odkazuje na pole `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="df4d5-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="df4d5-108">[out] Ukazatel na počet `ICorDebugValue` instancí vrácených ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="df4d5-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="df4d5-109">Tato hodnota může být null. Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="df4d5-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df4d5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df4d5-110">Requirements</span></span>  
 <span data-ttu-id="df4d5-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df4d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df4d5-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df4d5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df4d5-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df4d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df4d5-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df4d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4d5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="df4d5-115">See Also</span></span>  
    
 
