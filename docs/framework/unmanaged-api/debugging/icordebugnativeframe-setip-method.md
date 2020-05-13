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
ms.openlocfilehash: 786c0e7b38c74fd02dd6f7536af1899f295b0305
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206446"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="d9884-102">ICorDebugNativeFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="d9884-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="d9884-103">Nastaví ukazatel na instrukci na zadané umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="d9884-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9884-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9884-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9884-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9884-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="d9884-106">pro Umístění posunu v nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="d9884-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9884-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9884-107">Remarks</span></span>  
 <span data-ttu-id="d9884-108">Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9884-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="d9884-109">Pokud ladicí program potřebuje informace o snímku po volání `SetIP` , musí provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d9884-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="d9884-110">[ICorDebug](icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="d9884-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="d9884-111">Nicméně i v případě, že je rámec v platném stavu, je-li daný modul runtime, stále se může jednat o problémy, jako například neinicializované místní proměnné a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d9884-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="d9884-112">Volající je zodpovědný za pojištění soudržnosti běžícího programu.</span><span class="sxs-lookup"><span data-stu-id="d9884-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="d9884-113">Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` bloku nebo `finally` .</span><span class="sxs-lookup"><span data-stu-id="d9884-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="d9884-114">Pokud `SetIP` je volána k provedení takového přesunu na 64 platformě, vrátí HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="d9884-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9884-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9884-115">Requirements</span></span>  
 <span data-ttu-id="d9884-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9884-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9884-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9884-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9884-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d9884-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9884-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9884-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9884-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9884-120">See also</span></span>
