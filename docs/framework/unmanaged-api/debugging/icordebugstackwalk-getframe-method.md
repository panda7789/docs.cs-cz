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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111238"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="73234-102">ICorDebugStackWalk::GetFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="73234-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="73234-103">Získá aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="73234-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73234-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73234-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73234-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73234-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="73234-106">[in] Ukazatel na adresu vytvořeného orámovat objekt, který představuje aktuální rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73234-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73234-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73234-107">Return Value</span></span>  
 <span data-ttu-id="73234-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="73234-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73234-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73234-109">HRESULT</span></span>|<span data-ttu-id="73234-110">Popis</span><span class="sxs-lookup"><span data-stu-id="73234-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73234-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="73234-111">S_OK</span></span>|<span data-ttu-id="73234-112">Modul runtime byla úspěšně vrácena aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="73234-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="73234-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73234-113">E_FAIL</span></span>|<span data-ttu-id="73234-114">Aktuální rámec nebyl vrácen.</span><span class="sxs-lookup"><span data-stu-id="73234-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="73234-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="73234-115">S_FALSE</span></span>|<span data-ttu-id="73234-116">Aktuální rámec je příkaz nativní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="73234-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="73234-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73234-117">E_INVALIDARG</span></span>|`pFrame` <span data-ttu-id="73234-118">má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="73234-118">is null.</span></span>|  
|<span data-ttu-id="73234-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="73234-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="73234-120">Už na konec zásobníku; ukazatel na rámec Proto je možný žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="73234-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="73234-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="73234-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73234-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73234-122">Remarks</span></span>  
 `ICorDebugStackWalk` <span data-ttu-id="73234-123">Vrátí pouze skutečné rámců.</span><span class="sxs-lookup"><span data-stu-id="73234-123">returns only actual stack frames.</span></span> <span data-ttu-id="73234-124">Použití [icordebugthread3::getactiveinternalframes –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí interní snímků.</span><span class="sxs-lookup"><span data-stu-id="73234-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="73234-125">(Vnitřních rámcích datové struktury jsou vloženy do zásobníku modulem runtime k uložení dočasných dat..)</span><span class="sxs-lookup"><span data-stu-id="73234-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73234-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73234-126">Requirements</span></span>  
 <span data-ttu-id="73234-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73234-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73234-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73234-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73234-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73234-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="73234-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73234-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73234-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73234-131">See also</span></span>

- [<span data-ttu-id="73234-132">ICorDebugStackWalk – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73234-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="73234-133">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73234-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="73234-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="73234-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
