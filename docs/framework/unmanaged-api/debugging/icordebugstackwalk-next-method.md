---
title: ICorDebugStackWalk::Next – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 8cebb66ecf298eaaca0e7af23a9b8c6a2932c23f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131817"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="f7552-102">ICorDebugStackWalk::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f7552-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="f7552-103">Přesune objekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="f7552-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7552-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7552-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f7552-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7552-105">Return Value</span></span>  
 <span data-ttu-id="f7552-106">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="f7552-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f7552-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7552-107">HRESULT</span></span>|<span data-ttu-id="f7552-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f7552-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7552-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7552-109">S_OK</span></span>|<span data-ttu-id="f7552-110">Modul runtime se úspěšně rozvedl do dalšího snímku (viz poznámky).</span><span class="sxs-lookup"><span data-stu-id="f7552-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="f7552-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7552-111">E_FAIL</span></span>|<span data-ttu-id="f7552-112">Objekt `ICorDebugStackWalk` nelze Upřesnit.</span><span class="sxs-lookup"><span data-stu-id="f7552-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="f7552-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f7552-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="f7552-114">Byl dosažen konec zásobníku v důsledku tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="f7552-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="f7552-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f7552-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f7552-116">Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="f7552-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f7552-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f7552-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7552-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7552-118">Remarks</span></span>  
 <span data-ttu-id="f7552-119">Metoda `Next` přesune objekt `ICorDebugStackWalk` do volajícího rámce pouze v případě, že modul runtime může unwind aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="f7552-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="f7552-120">V opačném případě objekt přejde k dalšímu snímku, který může modul runtime vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="f7552-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7552-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7552-121">Requirements</span></span>  
 <span data-ttu-id="f7552-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7552-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7552-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7552-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7552-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f7552-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7552-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7552-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7552-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7552-126">See also</span></span>

- [<span data-ttu-id="f7552-127">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7552-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="f7552-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7552-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f7552-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="f7552-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
