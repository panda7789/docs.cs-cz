---
title: ICorDebugStackWalk::GetContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 700e0af05828b9fe0a50c1aac114e840adc276b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131853"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="b12e0-102">ICorDebugStackWalk::GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="b12e0-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="b12e0-103">Vrátí kontext pro aktuální rámec v objektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b12e0-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b12e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b12e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b12e0-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="b12e0-106">pro Příznaky, které označují požadovaný obsah vyrovnávací paměti kontextu (definované v souboru WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="b12e0-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="b12e0-107">pro Přidělená velikost vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="b12e0-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b12e0-108">mimo Skutečná velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="b12e0-108">[out] The actual size of the context.</span></span> <span data-ttu-id="b12e0-109">Tato hodnota musí být menší nebo rovna velikosti vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="b12e0-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="b12e0-110">mimo Vyrovnávací paměť kontextu.</span><span class="sxs-lookup"><span data-stu-id="b12e0-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b12e0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b12e0-111">Return Value</span></span>  
 <span data-ttu-id="b12e0-112">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="b12e0-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b12e0-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b12e0-113">HRESULT</span></span>|<span data-ttu-id="b12e0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b12e0-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b12e0-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b12e0-115">S_OK</span></span>|<span data-ttu-id="b12e0-116">Kontext pro aktuální rámec byl úspěšně vrácen.</span><span class="sxs-lookup"><span data-stu-id="b12e0-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="b12e0-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b12e0-117">E_FAIL</span></span>|<span data-ttu-id="b12e0-118">Kontext nelze vrátit.</span><span class="sxs-lookup"><span data-stu-id="b12e0-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="b12e0-119">HRESULT_FROM_WIN32 (VYROVNÁVACÍ PAMĚŤ ERROR_INSUFFICIENT)</span><span class="sxs-lookup"><span data-stu-id="b12e0-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="b12e0-120">Kontextová vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="b12e0-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="b12e0-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="b12e0-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="b12e0-122">Ukazatel na rámec je již na konci zásobníku; Proto nelze mít k dispozici žádné další snímky.</span><span class="sxs-lookup"><span data-stu-id="b12e0-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b12e0-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b12e0-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b12e0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b12e0-124">Remarks</span></span>  
 <span data-ttu-id="b12e0-125">Vzhledem k tomu, že unwinda obnoví pouze podmnožinu registrů, například nestálé Registry, kontext nemusí přesně odpovídat stavu registrace v době volání.</span><span class="sxs-lookup"><span data-stu-id="b12e0-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b12e0-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b12e0-126">Requirements</span></span>  
 <span data-ttu-id="b12e0-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12e0-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12e0-128">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b12e0-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b12e0-129">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b12e0-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b12e0-130">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12e0-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12e0-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b12e0-131">See also</span></span>

- [<span data-ttu-id="b12e0-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b12e0-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b12e0-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="b12e0-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
