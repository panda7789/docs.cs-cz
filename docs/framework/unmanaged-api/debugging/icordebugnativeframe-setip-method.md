---
title: ICorDebugNativeFrame::SetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 1d978cab0817af68356d95d635f8d2bfa3fd546a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096743"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="85796-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="85796-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="85796-103">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="85796-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85796-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85796-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85796-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85796-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="85796-106">pro Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="85796-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85796-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85796-107">Remarks</span></span>  
 <span data-ttu-id="85796-108">Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="85796-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="85796-109">Pokud ladicí program potřebuje informace o snímku po volání `SetIP`, musí provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="85796-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="85796-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="85796-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="85796-111">Nicméně i v případě, že je rámec v platném stavu, je-li daný modul runtime, stále se může jednat o problémy, jako například neinicializované místní proměnné a tak dále.</span><span class="sxs-lookup"><span data-stu-id="85796-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="85796-112">Volající je zodpovědný za pojištění soudržnosti běžícího programu.</span><span class="sxs-lookup"><span data-stu-id="85796-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="85796-113">Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="85796-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="85796-114">Pokud je volána `SetIP` k provedení tohoto přesunu na 64 platformě, vrátí HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="85796-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85796-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85796-115">Requirements</span></span>  
 <span data-ttu-id="85796-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85796-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85796-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85796-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85796-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85796-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85796-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85796-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85796-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85796-120">See also</span></span>
