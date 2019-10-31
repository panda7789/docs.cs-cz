---
title: ICorDebugILFrame::SetIP – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 60273d7cf91be04c5fc3041260e4bb146ce9a45e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095434"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="cecfb-102">ICorDebugILFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="cecfb-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="cecfb-103">Nastaví ukazatel na instrukci na zadané místo posunutí v kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="cecfb-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cecfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cecfb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cecfb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cecfb-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="cecfb-106">Umístění posunu v kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="cecfb-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cecfb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cecfb-107">Remarks</span></span>  
 <span data-ttu-id="cecfb-108">Volání `SetIP` okamžitě zruší platnost všech rámců a řetězů pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="cecfb-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="cecfb-109">Pokud ladicí program potřebuje informace o snímku po volání `SetIP`, musí provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cecfb-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="cecfb-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí zachovat rámec zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="cecfb-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="cecfb-111">Nicméně i v případě, že je rámec v platném stavu, mohou být stále problémy, jako například neinicializované místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="cecfb-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="cecfb-112">Volající je zodpovědný za zajištění návaznosti běžícího programu.</span><span class="sxs-lookup"><span data-stu-id="cecfb-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="cecfb-113">Na 64-bitových platformách nelze ukazatel na instrukci přesunout z `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="cecfb-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="cecfb-114">Pokud je volána `SetIP` k provedení tohoto přesunu na 64 platformě, vrátí HRESULT indikující selhání.</span><span class="sxs-lookup"><span data-stu-id="cecfb-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cecfb-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cecfb-115">Requirements</span></span>  
 <span data-ttu-id="cecfb-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cecfb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cecfb-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cecfb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cecfb-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cecfb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cecfb-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cecfb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
