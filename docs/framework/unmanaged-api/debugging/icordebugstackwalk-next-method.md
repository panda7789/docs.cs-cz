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
ms.openlocfilehash: b89e968e9b12943c8192af3b280f8bd321a02110
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378794"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="03051-102">ICorDebugStackWalk::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="03051-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="03051-103">Přesune objekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) k dalšímu snímku.</span><span class="sxs-lookup"><span data-stu-id="03051-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03051-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03051-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="03051-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="03051-105">Return Value</span></span>  
 <span data-ttu-id="03051-106">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="03051-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="03051-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03051-107">HRESULT</span></span>|<span data-ttu-id="03051-108">Popis</span><span class="sxs-lookup"><span data-stu-id="03051-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03051-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="03051-109">S_OK</span></span>|<span data-ttu-id="03051-110">Modul runtime se úspěšně rozvedl do dalšího snímku (viz poznámky).</span><span class="sxs-lookup"><span data-stu-id="03051-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="03051-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03051-111">E_FAIL</span></span>|<span data-ttu-id="03051-112">`ICorDebugStackWalk`Objekt nelze Upřesnit.</span><span class="sxs-lookup"><span data-stu-id="03051-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="03051-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="03051-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="03051-114">Byl dosažen konec zásobníku v důsledku tohoto unwind.</span><span class="sxs-lookup"><span data-stu-id="03051-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="03051-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="03051-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="03051-116">Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="03051-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="03051-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="03051-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03051-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03051-118">Remarks</span></span>  
 <span data-ttu-id="03051-119">`Next`Metoda přesune `ICorDebugStackWalk` objekt do volajícího rámce pouze v případě, že modul runtime může unwind aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="03051-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="03051-120">V opačném případě objekt přejde k dalšímu snímku, který může modul runtime vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="03051-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03051-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03051-121">Requirements</span></span>  
 <span data-ttu-id="03051-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03051-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03051-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03051-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03051-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="03051-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03051-125">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03051-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03051-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="03051-126">See also</span></span>

- [<span data-ttu-id="03051-127">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03051-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="03051-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03051-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="03051-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="03051-129">Debugging</span></span>](index.md)
