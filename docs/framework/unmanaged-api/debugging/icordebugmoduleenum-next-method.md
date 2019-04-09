---
title: ICorDebugModuleEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa341c726ba84dc1d12b6c5628253a100d65a719
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167099"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="4b0c4-102">ICorDebugModuleEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4b0c4-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="4b0c4-103">Získá počet instancí "ICorDebugModule" určené `celt` z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="4b0c4-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b0c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b0c4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b0c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b0c4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4b0c4-106">[in] Počet `ICorDebugModule` instancí, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="4b0c4-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="4b0c4-107">[out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugModule` objektu.</span><span class="sxs-lookup"><span data-stu-id="4b0c4-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4b0c4-108">[out] Ukazatel na počet `ICorDebugModule` skutečně vrácených instancí.</span><span class="sxs-lookup"><span data-stu-id="4b0c4-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="4b0c4-109">Tato hodnota může mít hodnotu null Pokud `celt` je jedna.</span><span class="sxs-lookup"><span data-stu-id="4b0c4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b0c4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b0c4-110">Requirements</span></span>  
 <span data-ttu-id="4b0c4-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b0c4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0c4-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b0c4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b0c4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b0c4-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4b0c4-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4b0c4-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b0c4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b0c4-115">See also</span></span>
