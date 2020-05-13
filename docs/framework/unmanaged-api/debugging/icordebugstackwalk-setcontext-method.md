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
ms.openlocfilehash: 896e797acc76e8d8034bd964e488317a62eed97b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378778"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="2e48f-102">ICorDebugStackWalk::SetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="2e48f-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="2e48f-103">Nastaví aktuální kontext objektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) na platný kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e48f-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e48f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e48f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e48f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e48f-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="2e48f-106">pro Příznak [CorDebugSetContextFlag –](cordebugsetcontextflag-enumeration.md) , který označuje, zda je kontext z aktivního rámce v zásobníku, nebo kontext získaný odvinutím zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2e48f-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2e48f-107">pro Přidělená velikost `CONTEXT` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e48f-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="2e48f-108">pro `CONTEXT`Vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="2e48f-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e48f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e48f-109">Return Value</span></span>  
 <span data-ttu-id="2e48f-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2e48f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2e48f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e48f-111">HRESULT</span></span>|<span data-ttu-id="2e48f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2e48f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e48f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e48f-113">S_OK</span></span>|<span data-ttu-id="2e48f-114">`ICorDebugStackWalk`Kontext objektu byl úspěšně nastaven.</span><span class="sxs-lookup"><span data-stu-id="2e48f-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="2e48f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e48f-115">E_FAIL</span></span>|<span data-ttu-id="2e48f-116">`ICorDebugStackWalk`Kontext objektu nebyl nastaven.</span><span class="sxs-lookup"><span data-stu-id="2e48f-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="2e48f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2e48f-117">E_INVALIDARG</span></span>|<span data-ttu-id="2e48f-118">Kontext má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2e48f-118">The context is null.</span></span>|  
|<span data-ttu-id="2e48f-119">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="2e48f-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="2e48f-120">Kontextová vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="2e48f-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2e48f-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="2e48f-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e48f-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e48f-122">Remarks</span></span>  
 <span data-ttu-id="2e48f-123">Tato metoda nemění aktuální kontext vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e48f-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="2e48f-124">Nastavení aktuálního kontextu na neplatný kontext může způsobit nepředvídatelné výsledky z Stack prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="2e48f-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="2e48f-125">Přesnou bitovou kopii tohoto kontextu lze načíst ihned voláním metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e48f-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e48f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e48f-126">Requirements</span></span>  
 <span data-ttu-id="2e48f-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e48f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e48f-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e48f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e48f-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e48f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e48f-130">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e48f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e48f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e48f-131">See also</span></span>

- [<span data-ttu-id="2e48f-132">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e48f-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2e48f-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="2e48f-133">Debugging</span></span>](index.md)
