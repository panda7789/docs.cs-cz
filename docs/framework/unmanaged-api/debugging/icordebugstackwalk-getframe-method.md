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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 253a25fdfc1f00adbc20388660caf6c227030a1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782730"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="0c162-102">ICorDebugStackWalk::GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="0c162-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="0c162-103">Získá aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="0c162-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c162-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c162-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c162-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c162-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="0c162-106">[in] Ukazatel na adresu vytvořeného orámovat objekt, který představuje aktuální rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0c162-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c162-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0c162-107">Return Value</span></span>  
 <span data-ttu-id="0c162-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0c162-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0c162-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c162-109">HRESULT</span></span>|<span data-ttu-id="0c162-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0c162-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c162-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c162-111">S_OK</span></span>|<span data-ttu-id="0c162-112">Modul runtime byla úspěšně vrácena aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="0c162-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="0c162-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c162-113">E_FAIL</span></span>|<span data-ttu-id="0c162-114">Aktuální rámec nebyl vrácen.</span><span class="sxs-lookup"><span data-stu-id="0c162-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="0c162-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0c162-115">S_FALSE</span></span>|<span data-ttu-id="0c162-116">Aktuální rámec je příkaz nativní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0c162-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="0c162-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0c162-117">E_INVALIDARG</span></span>|<span data-ttu-id="0c162-118">`pFrame` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0c162-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="0c162-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="0c162-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="0c162-120">Už na konec zásobníku; ukazatel na rámec Proto je možný žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="0c162-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0c162-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0c162-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c162-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c162-122">Remarks</span></span>  
 <span data-ttu-id="0c162-123">`ICorDebugStackWalk` Vrátí pouze skutečné rámců.</span><span class="sxs-lookup"><span data-stu-id="0c162-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="0c162-124">Použití [icordebugthread3::getactiveinternalframes –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí interní snímků.</span><span class="sxs-lookup"><span data-stu-id="0c162-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="0c162-125">(Vnitřních rámcích datové struktury jsou vloženy do zásobníku modulem runtime k uložení dočasných dat..)</span><span class="sxs-lookup"><span data-stu-id="0c162-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c162-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c162-126">Requirements</span></span>  
 <span data-ttu-id="0c162-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c162-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c162-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c162-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c162-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c162-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c162-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c162-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c162-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c162-131">See also</span></span>

- [<span data-ttu-id="0c162-132">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c162-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="0c162-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0c162-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0c162-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="0c162-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
