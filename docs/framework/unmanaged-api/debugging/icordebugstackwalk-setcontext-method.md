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
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131815"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="2c888-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="2c888-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="2c888-103">Nastaví aktuální kontext objektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) na platný kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="2c888-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c888-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c888-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c888-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c888-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="2c888-106">pro Příznak [CorDebugSetContextFlag –](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) , který označuje, zda je kontext z aktivního rámce v zásobníku, nebo kontext získaný odvinutím zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2c888-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2c888-107">pro Přidělená velikost vyrovnávací paměti `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="2c888-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="2c888-108">pro Vyrovnávací paměť `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="2c888-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c888-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c888-109">Return Value</span></span>  
 <span data-ttu-id="2c888-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2c888-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2c888-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c888-111">HRESULT</span></span>|<span data-ttu-id="2c888-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2c888-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c888-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c888-113">S_OK</span></span>|<span data-ttu-id="2c888-114">Kontext objektu `ICorDebugStackWalk` byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="2c888-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="2c888-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c888-115">E_FAIL</span></span>|<span data-ttu-id="2c888-116">Kontext `ICorDebugStackWalk`ho objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="2c888-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="2c888-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2c888-117">E_INVALIDARG</span></span>|<span data-ttu-id="2c888-118">Kontext má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2c888-118">The context is null.</span></span>|  
|<span data-ttu-id="2c888-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="2c888-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="2c888-120">Kontextová vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="2c888-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2c888-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2c888-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c888-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c888-122">Remarks</span></span>  
 <span data-ttu-id="2c888-123">Tato metoda nemění aktuální kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="2c888-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="2c888-124">Nastavení aktuálního kontextu na neplatný kontext může způsobit nepředvídatelné výsledky z Stack prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="2c888-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="2c888-125">Přesnou bitovou kopii tohoto kontextu lze načíst ihned voláním metody [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2c888-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c888-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c888-126">Requirements</span></span>  
 <span data-ttu-id="2c888-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c888-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c888-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c888-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c888-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c888-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c888-130">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c888-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c888-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c888-131">See also</span></span>

- [<span data-ttu-id="2c888-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2c888-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2c888-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="2c888-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
