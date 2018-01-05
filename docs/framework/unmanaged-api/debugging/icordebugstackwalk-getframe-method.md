---
title: "ICorDebugStackWalk::GetFrame – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c095afd0513360876e5330a130a4d938e30f8db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="f9102-102">ICorDebugStackWalk::GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="f9102-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="f9102-103">Získá aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f9102-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9102-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9102-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9102-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9102-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="f9102-106">[v] Ukazatel na adresu objektu vytvořené rámce, který představuje aktuální rámečku v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f9102-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9102-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f9102-107">Return Value</span></span>  
 <span data-ttu-id="f9102-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="f9102-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f9102-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9102-109">HRESULT</span></span>|<span data-ttu-id="f9102-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f9102-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9102-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9102-111">S_OK</span></span>|<span data-ttu-id="f9102-112">Modul runtime byla úspěšně vrácena aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="f9102-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="f9102-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9102-113">E_FAIL</span></span>|<span data-ttu-id="f9102-114">Aktuální snímek nebyla vrácena.</span><span class="sxs-lookup"><span data-stu-id="f9102-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="f9102-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f9102-115">S_FALSE</span></span>|<span data-ttu-id="f9102-116">Aktuální snímek je nativní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f9102-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="f9102-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9102-117">E_INVALIDARG</span></span>|<span data-ttu-id="f9102-118">`pFrame`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f9102-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="f9102-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="f9102-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="f9102-120">Ukazatel na rámec je již na konec zásobníku; Proto je přístupná žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="f9102-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f9102-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f9102-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9102-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9102-122">Remarks</span></span>  
 <span data-ttu-id="f9102-123">`ICorDebugStackWalk`Vrátí pouze rámce skutečné zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f9102-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="f9102-124">Použití [icordebugthread3::getactiveinternalframes –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí interní rámce.</span><span class="sxs-lookup"><span data-stu-id="f9102-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="f9102-125">(Interní rámce jsou vloženy do zásobníku modulem runtime pro uložení dočasných dat datové struktury).</span><span class="sxs-lookup"><span data-stu-id="f9102-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9102-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9102-126">Requirements</span></span>  
 <span data-ttu-id="f9102-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9102-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9102-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9102-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9102-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9102-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9102-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9102-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9102-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9102-131">See Also</span></span>  
 [<span data-ttu-id="f9102-132">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9102-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="f9102-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f9102-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f9102-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="f9102-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
