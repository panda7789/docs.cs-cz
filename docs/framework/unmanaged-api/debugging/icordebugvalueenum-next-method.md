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
ms.openlocfilehash: 2ae09b4f1cd069edf81be583c7c4226717736094
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764272"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="93c57-102">ICorDebugValueEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="93c57-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="93c57-103">Získá zadaný počet instancí "ICorDebugValue" z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="93c57-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c57-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93c57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93c57-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="93c57-106">[in] Počet `ICorDebugValue` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="93c57-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="93c57-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="93c57-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="93c57-108">[out] Ukazatel na počet `ICorDebugValue` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="93c57-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="93c57-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="93c57-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93c57-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93c57-110">Requirements</span></span>  
 <span data-ttu-id="93c57-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93c57-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93c57-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93c57-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93c57-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93c57-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93c57-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93c57-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c57-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93c57-115">See also</span></span>
