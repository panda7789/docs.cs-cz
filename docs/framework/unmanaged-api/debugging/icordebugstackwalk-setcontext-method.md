---
title: "ICorDebugStackWalk::SetContext – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00e278df2b23d6fddb18c24eefb3f2aa4d1cc3cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="a95d0-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="a95d0-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="a95d0-103">Nastaví [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) aktuální kontext objektu, který má platný kontext pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="a95d0-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a95d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a95d0-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a95d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a95d0-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="a95d0-106">[v] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) příznak, který určuje, zda kontext je z aktivního rámce v zásobníku nebo získat unwinding zásobníku v kontextu.</span><span class="sxs-lookup"><span data-stu-id="a95d0-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="a95d0-107">[v] Přidělenou velikost `CONTEXT` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a95d0-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="a95d0-108">[v] `CONTEXT` Vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a95d0-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a95d0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a95d0-109">Return Value</span></span>  
 <span data-ttu-id="a95d0-110">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="a95d0-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a95d0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a95d0-111">HRESULT</span></span>|<span data-ttu-id="a95d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a95d0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a95d0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a95d0-113">S_OK</span></span>|<span data-ttu-id="a95d0-114">`ICorDebugStackWalk` Objektu kontext byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="a95d0-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="a95d0-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a95d0-115">E_FAIL</span></span>|<span data-ttu-id="a95d0-116">`ICorDebugStackWalk` Kontext objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="a95d0-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="a95d0-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a95d0-117">E_INVALIDARG</span></span>|<span data-ttu-id="a95d0-118">Kontext má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a95d0-118">The context is null.</span></span>|  
|<span data-ttu-id="a95d0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="a95d0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="a95d0-120">Vyrovnávací paměti kontextu je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="a95d0-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a95d0-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="a95d0-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a95d0-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a95d0-122">Remarks</span></span>  
 <span data-ttu-id="a95d0-123">Tato metoda nezmění aktuální kontext vlákno.</span><span class="sxs-lookup"><span data-stu-id="a95d0-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="a95d0-124">Nastavení aktuální kontext ke kontextu neplatný může způsobit nepředvídatelné výsledky z walkera zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a95d0-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="a95d0-125">Přesná bitové kopie tohoto kontextu můžete načíst okamžitě voláním [icordebugstackwalk::getcontext –](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a95d0-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a95d0-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a95d0-126">Requirements</span></span>  
 <span data-ttu-id="a95d0-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a95d0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a95d0-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a95d0-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a95d0-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a95d0-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a95d0-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a95d0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a95d0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a95d0-131">See Also</span></span>  
 [<span data-ttu-id="a95d0-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a95d0-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a95d0-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="a95d0-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
