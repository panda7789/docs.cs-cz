---
title: ICorDebugStackWalk::GetFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131842"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="09b85-102">ICorDebugStackWalk::GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="09b85-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="09b85-103">Načte aktuální rámec v objektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="09b85-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09b85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09b85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09b85-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="09b85-106">pro Ukazatel na adresu vytvořeného objektu Frame, který představuje aktuální rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="09b85-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09b85-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="09b85-107">Return Value</span></span>  
 <span data-ttu-id="09b85-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="09b85-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="09b85-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09b85-109">HRESULT</span></span>|<span data-ttu-id="09b85-110">Popis</span><span class="sxs-lookup"><span data-stu-id="09b85-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09b85-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="09b85-111">S_OK</span></span>|<span data-ttu-id="09b85-112">Modul runtime úspěšně vrátil aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="09b85-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="09b85-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09b85-113">E_FAIL</span></span>|<span data-ttu-id="09b85-114">Aktuální rámec nebyl vrácen.</span><span class="sxs-lookup"><span data-stu-id="09b85-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="09b85-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="09b85-115">S_FALSE</span></span>|<span data-ttu-id="09b85-116">Aktuální rámec je nativní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="09b85-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="09b85-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="09b85-117">E_INVALIDARG</span></span>|<span data-ttu-id="09b85-118">`pFrame` je null.</span><span class="sxs-lookup"><span data-stu-id="09b85-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="09b85-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="09b85-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="09b85-120">Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="09b85-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="09b85-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="09b85-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b85-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09b85-122">Remarks</span></span>  
 <span data-ttu-id="09b85-123">`ICorDebugStackWalk` vrátí pouze skutečné rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="09b85-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="09b85-124">K vrácení vnitřních rámců použijte metodu [ICorDebugThread3:: GetActiveInternalFrames –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09b85-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="09b85-125">(Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.)</span><span class="sxs-lookup"><span data-stu-id="09b85-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b85-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="09b85-126">Requirements</span></span>  
 <span data-ttu-id="09b85-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b85-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b85-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09b85-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09b85-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09b85-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09b85-130">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b85-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b85-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09b85-131">See also</span></span>

- [<span data-ttu-id="09b85-132">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="09b85-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="09b85-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="09b85-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="09b85-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="09b85-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
