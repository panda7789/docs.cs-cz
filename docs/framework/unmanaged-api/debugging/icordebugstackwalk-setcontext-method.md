---
title: "ICorDebugStackWalk::SetContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374092c500d4263a172219c38cbc1b2f0ce293a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="563de-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="563de-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="563de-103">Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu, který má platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="563de-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="563de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="563de-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="563de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="563de-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="563de-106">[v] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který určuje, zda kontext je z aktivního rámce v zásobníku nebo získat unwinding zásobníku v kontextu.</span><span class="sxs-lookup"><span data-stu-id="563de-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="563de-107">[v] Přidělenou velikost `CONTEXT` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="563de-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="563de-108">[v] `CONTEXT` Vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="563de-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="563de-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="563de-109">Return Value</span></span>  
 <span data-ttu-id="563de-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="563de-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="563de-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="563de-111">HRESULT</span></span>|<span data-ttu-id="563de-112">Popis</span><span class="sxs-lookup"><span data-stu-id="563de-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="563de-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="563de-113">S_OK</span></span>|<span data-ttu-id="563de-114">`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="563de-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="563de-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="563de-115">E_FAIL</span></span>|<span data-ttu-id="563de-116">`ICorDebugStackWalk` Kontext objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="563de-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="563de-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="563de-117">E_INVALIDARG</span></span>|<span data-ttu-id="563de-118">Kontext má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="563de-118">The context is null.</span></span>|  
|<span data-ttu-id="563de-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="563de-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="563de-120">Vyrovnávací paměti kontextu je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="563de-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="563de-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="563de-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="563de-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="563de-122">Remarks</span></span>  
 <span data-ttu-id="563de-123">Tato metoda nezmění aktuální kontext vlákno.</span><span class="sxs-lookup"><span data-stu-id="563de-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="563de-124">Nastavení aktuální kontext ke kontextu neplatný může způsobit nepředvídatelné výsledky z walkera zásobníku.</span><span class="sxs-lookup"><span data-stu-id="563de-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="563de-125">Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="563de-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="563de-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="563de-126">Requirements</span></span>  
 <span data-ttu-id="563de-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="563de-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="563de-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="563de-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="563de-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="563de-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="563de-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="563de-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563de-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="563de-131">See Also</span></span>  
 [<span data-ttu-id="563de-132">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="563de-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="563de-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="563de-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
