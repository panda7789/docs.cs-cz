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
ms.openlocfilehash: 604486a074c3dbe3d19b741df28499ee03e1b2e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193275"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="bbefa-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="bbefa-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="bbefa-103">Nastaví ukazatele na instrukci do zadaného umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="bbefa-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbefa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbefa-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbefa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbefa-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="bbefa-106">[in] Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="bbefa-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbefa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbefa-107">Remarks</span></span>  
 <span data-ttu-id="bbefa-108">Volání `SetIP` okamžitě zneplatnit všechny rámce a řetězce pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="bbefa-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="bbefa-109">Pokud ladicí program potřebuje informace o snímcích po volání `SetIP`, je nutné provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bbefa-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="bbefa-110">[Icordebug –](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="bbefa-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="bbefa-111">Ale i v případě, že rámec je v platném stavu, co se týče modul runtime, stále může existovat problémy, jako je například neinicializovaných místních proměnných a tak dále.</span><span class="sxs-lookup"><span data-stu-id="bbefa-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="bbefa-112">Volající zodpovídá za pojištění integrita spuštěný program.</span><span class="sxs-lookup"><span data-stu-id="bbefa-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="bbefa-113">Na 64bitových platformách, ukazatele na instrukci nelze přesunout z celkového počtu `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="bbefa-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="bbefa-114">Pokud `SetIP` nazývá provést přesun na 64bitové platformě, vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="bbefa-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbefa-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbefa-115">Requirements</span></span>  
 <span data-ttu-id="bbefa-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbefa-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbefa-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbefa-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbefa-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbefa-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bbefa-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bbefa-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbefa-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbefa-120">See also</span></span>
