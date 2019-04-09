---
title: ICorDebugStackWalk::SetContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116464"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="400eb-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="400eb-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="400eb-103">Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu na platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="400eb-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="400eb-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="400eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="400eb-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="400eb-106">[in] A [cordebugsetcontextflag –](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který označuje, zda je kontext z aktivní rámec v zásobníku nebo kontext získané odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="400eb-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="400eb-107">[in] Přidělená velikost `CONTEXT` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="400eb-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="400eb-108">[in] `CONTEXT` Vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="400eb-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="400eb-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="400eb-109">Return Value</span></span>  
 <span data-ttu-id="400eb-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="400eb-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="400eb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="400eb-111">HRESULT</span></span>|<span data-ttu-id="400eb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="400eb-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="400eb-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="400eb-113">S_OK</span></span>|<span data-ttu-id="400eb-114">`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="400eb-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="400eb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="400eb-115">E_FAIL</span></span>|<span data-ttu-id="400eb-116">`ICorDebugStackWalk` Kontext objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="400eb-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="400eb-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="400eb-117">E_INVALIDARG</span></span>|<span data-ttu-id="400eb-118">Kontext je null.</span><span class="sxs-lookup"><span data-stu-id="400eb-118">The context is null.</span></span>|  
|<span data-ttu-id="400eb-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="400eb-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="400eb-120">Kontext vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="400eb-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="400eb-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="400eb-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="400eb-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="400eb-122">Remarks</span></span>  
 <span data-ttu-id="400eb-123">Tato metoda nezmění kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="400eb-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="400eb-124">Nastavení aktuálního kontextu Neplatný kontext může způsobit nepředvídatelné výsledky z zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="400eb-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="400eb-125">Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="400eb-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="400eb-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="400eb-126">Requirements</span></span>  
 <span data-ttu-id="400eb-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="400eb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="400eb-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="400eb-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="400eb-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="400eb-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="400eb-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="400eb-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="400eb-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="400eb-131">See also</span></span>

- [<span data-ttu-id="400eb-132">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="400eb-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="400eb-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="400eb-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
