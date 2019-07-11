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
ms.openlocfilehash: d6eb97fc70fec25f4b225c3fd5bad1e780091f7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771032"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="d8314-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="d8314-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="d8314-103">Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu na platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="d8314-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8314-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8314-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8314-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8314-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="d8314-106">[in] A [cordebugsetcontextflag –](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který označuje, zda je kontext z aktivní rámec v zásobníku nebo kontext získané odvíjení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d8314-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d8314-107">[in] Přidělená velikost `CONTEXT` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d8314-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="d8314-108">[in] `CONTEXT` Vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d8314-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8314-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d8314-109">Return Value</span></span>  
 <span data-ttu-id="d8314-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="d8314-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d8314-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8314-111">HRESULT</span></span>|<span data-ttu-id="d8314-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d8314-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8314-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8314-113">S_OK</span></span>|<span data-ttu-id="d8314-114">`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="d8314-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="d8314-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8314-115">E_FAIL</span></span>|<span data-ttu-id="d8314-116">`ICorDebugStackWalk` Kontext objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="d8314-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="d8314-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d8314-117">E_INVALIDARG</span></span>|<span data-ttu-id="d8314-118">Kontext je null.</span><span class="sxs-lookup"><span data-stu-id="d8314-118">The context is null.</span></span>|  
|<span data-ttu-id="d8314-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="d8314-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="d8314-120">Kontext vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="d8314-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d8314-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="d8314-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8314-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8314-122">Remarks</span></span>  
 <span data-ttu-id="d8314-123">Tato metoda nezmění kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="d8314-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="d8314-124">Nastavení aktuálního kontextu Neplatný kontext může způsobit nepředvídatelné výsledky z zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="d8314-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="d8314-125">Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d8314-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8314-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8314-126">Requirements</span></span>  
 <span data-ttu-id="d8314-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8314-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8314-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8314-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8314-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8314-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8314-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8314-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8314-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8314-131">See also</span></span>

- [<span data-ttu-id="d8314-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d8314-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d8314-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="d8314-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
