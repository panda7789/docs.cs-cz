---
title: "ICorDebugStackWalk::Next – metoda"
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
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="60806-102">ICorDebugStackWalk::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="60806-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="60806-103">Přesune [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu na další snímek.</span><span class="sxs-lookup"><span data-stu-id="60806-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60806-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60806-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="60806-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60806-105">Return Value</span></span>  
 <span data-ttu-id="60806-106">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="60806-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="60806-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60806-107">HRESULT</span></span>|<span data-ttu-id="60806-108">Popis</span><span class="sxs-lookup"><span data-stu-id="60806-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60806-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="60806-109">S_OK</span></span>|<span data-ttu-id="60806-110">Modul runtime úspěšně odděleny na další snímek (viz poznámky).</span><span class="sxs-lookup"><span data-stu-id="60806-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="60806-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60806-111">E_FAIL</span></span>|<span data-ttu-id="60806-112">`ICorDebugStackWalk` Objekt nelze rozšířené.</span><span class="sxs-lookup"><span data-stu-id="60806-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="60806-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="60806-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="60806-114">V důsledku této unwind byl dosažen konec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="60806-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="60806-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="60806-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="60806-116">Ukazatel na rámec je již na konec zásobníku; Proto je přístupná žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="60806-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="60806-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="60806-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60806-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60806-118">Remarks</span></span>  
 <span data-ttu-id="60806-119">`Next` Metoda záloh `ICorDebugStackWalk` do volání rámečku objektu pouze v případě, že modul runtime můžete unwind aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="60806-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="60806-120">Objekt, jinak hodnota přejde na další snímek, který je schopen unwind modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="60806-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60806-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60806-121">Requirements</span></span>  
 <span data-ttu-id="60806-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60806-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60806-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60806-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60806-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60806-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60806-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60806-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60806-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="60806-126">See Also</span></span>  
 [<span data-ttu-id="60806-127">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60806-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="60806-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="60806-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="60806-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="60806-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
