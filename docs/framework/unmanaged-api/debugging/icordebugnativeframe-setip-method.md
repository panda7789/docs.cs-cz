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
ms.openlocfilehash: bc33768e4155a0e272d3374d4c586c79ef2ff3fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792782"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="aac03-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="aac03-103">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="aac03-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aac03-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aac03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aac03-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="aac03-106">pro Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="aac03-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac03-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aac03-107">Remarks</span></span>  
 <span data-ttu-id="aac03-108">Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="aac03-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="aac03-109">Pokud ladicí program potřebuje informace o snímku po volání `SetIP`, musí provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aac03-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="aac03-110">[ICorDebug](icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="aac03-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="aac03-111">Nicméně i v případě, že je rámec v platném stavu, je-li daný modul runtime, stále se může jednat o problémy, jako například neinicializované místní proměnné a tak dále.</span><span class="sxs-lookup"><span data-stu-id="aac03-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="aac03-112">Volající je zodpovědný za pojištění soudržnosti běžícího programu.</span><span class="sxs-lookup"><span data-stu-id="aac03-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="aac03-113">Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="aac03-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="aac03-114">Pokud je volána `SetIP` k provedení tohoto přesunu na 64 platformě, vrátí HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="aac03-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac03-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aac03-115">Requirements</span></span>  
 <span data-ttu-id="aac03-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aac03-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac03-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aac03-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aac03-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aac03-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aac03-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac03-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac03-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aac03-120">See also</span></span>
