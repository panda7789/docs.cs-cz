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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba1e6c113fb4caa0db8963e238d3eceba0cc8ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224855"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="47f37-102">ICorDebugStackWalk::GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="47f37-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="47f37-103">Vrátí kontext pro aktuální rámec v [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="47f37-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47f37-104">Syntax</span></span>  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47f37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47f37-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="47f37-106">[in] Příznaky, které určují požadovaný obsah vyrovnávací paměti kontextu (definované v souboru WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="47f37-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="47f37-107">[in] Přidělená velikost vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="47f37-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="47f37-108">[out] Skutečná velikost kontextu.</span><span class="sxs-lookup"><span data-stu-id="47f37-108">[out] The actual size of the context.</span></span> <span data-ttu-id="47f37-109">Tato hodnota musí být menší než nebo roven velikosti vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="47f37-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="47f37-110">[out] Vyrovnávací paměti kontextu.</span><span class="sxs-lookup"><span data-stu-id="47f37-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47f37-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="47f37-111">Return Value</span></span>  
 <span data-ttu-id="47f37-112">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="47f37-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47f37-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47f37-113">HRESULT</span></span>|<span data-ttu-id="47f37-114">Popis</span><span class="sxs-lookup"><span data-stu-id="47f37-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47f37-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="47f37-115">S_OK</span></span>|<span data-ttu-id="47f37-116">Kontext pro aktuální rámec byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="47f37-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="47f37-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47f37-117">E_FAIL</span></span>|<span data-ttu-id="47f37-118">Nebylo možné vrátit kontext.</span><span class="sxs-lookup"><span data-stu-id="47f37-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="47f37-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="47f37-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="47f37-120">Kontext vyrovnávací paměť je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="47f37-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="47f37-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="47f37-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="47f37-122">Už na konec zásobníku; ukazatel na rámec Proto je možný žádné další rámce.</span><span class="sxs-lookup"><span data-stu-id="47f37-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="47f37-123">Výjimky</span><span class="sxs-lookup"><span data-stu-id="47f37-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47f37-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47f37-124">Remarks</span></span>  
 <span data-ttu-id="47f37-125">Protože odvíjení obnoví pouze podmnožinu registrů, jako je například stálé registrů kontextu nemusí přesně odpovídat stav registru v době volání.</span><span class="sxs-lookup"><span data-stu-id="47f37-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f37-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47f37-126">Requirements</span></span>  
 <span data-ttu-id="47f37-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47f37-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f37-128">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47f37-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47f37-129">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47f37-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47f37-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47f37-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f37-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47f37-131">See also</span></span>

- [<span data-ttu-id="47f37-132">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="47f37-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="47f37-133">Ladění</span><span class="sxs-lookup"><span data-stu-id="47f37-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
