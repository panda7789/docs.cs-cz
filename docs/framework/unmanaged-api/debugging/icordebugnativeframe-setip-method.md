---
title: "ICorDebugNativeFrame::SetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25b4f42eb6f10ecade468824d9d790a2bce740a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="9f70b-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="9f70b-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="9f70b-103">Nastaví ukazatel instrukce do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="9f70b-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f70b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f70b-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f70b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f70b-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="9f70b-106">[v] Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="9f70b-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f70b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f70b-107">Remarks</span></span>  
 <span data-ttu-id="9f70b-108">Volání `SetIP` okamžitě zneplatní všechny snímky a řetězy pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="9f70b-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="9f70b-109">Pokud ladicí program musí rámce informace po volání `SetIP`, je třeba provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9f70b-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="9f70b-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="9f70b-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="9f70b-111">Ale i pokud rámečku není v platném stavu, co se týče modulu runtime, stále může mít problémy, jako je například neinicializovaných místních proměnných a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9f70b-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="9f70b-112">Volající zodpovídá za pojištění integrita spuštěného programu.</span><span class="sxs-lookup"><span data-stu-id="9f70b-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="9f70b-113">Na 64bitových platformách, nelze jej přesunout ukazatel instrukce mimo `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="9f70b-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="9f70b-114">Pokud `SetIP` nazývá aby přesunu na 64bitové platformě, vrátí HRESULT udávající neúspěch.</span><span class="sxs-lookup"><span data-stu-id="9f70b-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f70b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f70b-115">Requirements</span></span>  
 <span data-ttu-id="9f70b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f70b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f70b-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f70b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f70b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f70b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f70b-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f70b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f70b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f70b-120">See Also</span></span>  
 
