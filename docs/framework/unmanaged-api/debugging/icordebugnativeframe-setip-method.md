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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed8b6bf60790c10b9869dcc41678be050b8979dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420222"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="00ff1-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="00ff1-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="00ff1-103">Nastaví ukazatel instrukce do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="00ff1-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ff1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00ff1-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00ff1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00ff1-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="00ff1-106">[v] Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="00ff1-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00ff1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00ff1-107">Remarks</span></span>  
 <span data-ttu-id="00ff1-108">Volání `SetIP` okamžitě zneplatní všechny snímky a řetězy pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="00ff1-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="00ff1-109">Pokud ladicí program musí rámce informace po volání `SetIP`, je třeba provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="00ff1-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="00ff1-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="00ff1-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="00ff1-111">Ale i pokud rámečku není v platném stavu, co se týče modulu runtime, stále může mít problémy, jako je například neinicializovaných místních proměnných a tak dále.</span><span class="sxs-lookup"><span data-stu-id="00ff1-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="00ff1-112">Volající zodpovídá za pojištění integrita spuštěného programu.</span><span class="sxs-lookup"><span data-stu-id="00ff1-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="00ff1-113">Na 64bitových platformách, nelze jej přesunout ukazatel instrukce mimo `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="00ff1-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="00ff1-114">Pokud `SetIP` nazývá aby přesunu na 64bitové platformě, vrátí HRESULT udávající neúspěch.</span><span class="sxs-lookup"><span data-stu-id="00ff1-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ff1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00ff1-115">Requirements</span></span>  
 <span data-ttu-id="00ff1-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00ff1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00ff1-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00ff1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00ff1-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00ff1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00ff1-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00ff1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ff1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="00ff1-120">See Also</span></span>  
 
