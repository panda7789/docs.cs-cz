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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2af3f58fa7714b3c2b0ba387b1da650f0638dd6c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758772"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="0b8a9-102">ICorDebugILFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="0b8a9-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="0b8a9-103">Nastaví ukazatele na instrukci do zadaného umístění posunu v kódu Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="0b8a9-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b8a9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b8a9-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="0b8a9-106">Umístění posunu v kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b8a9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b8a9-107">Remarks</span></span>  
 <span data-ttu-id="0b8a9-108">Volání `SetIP` okamžitě zneplatnit všechny rámce a řetězce pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="0b8a9-109">Pokud ladicí program potřebuje informace o snímcích po volání `SetIP`, je nutné provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="0b8a9-110">[Icordebug –](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="0b8a9-111">Ale i v případě, že rámec je příkaz v platném stavu, stále může existovat problémy, jako je neinicializovaných místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="0b8a9-112">Volající zodpovídá za to integrita spuštěný program.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="0b8a9-113">Na 64bitových platformách, ukazatele na instrukci nelze přesunout z celkového počtu `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="0b8a9-114">Pokud `SetIP` nazývá provést přesun na 64bitové platformě, vrátí HRESULT označující selhání.</span><span class="sxs-lookup"><span data-stu-id="0b8a9-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8a9-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b8a9-115">Requirements</span></span>  
 <span data-ttu-id="0b8a9-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b8a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8a9-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b8a9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b8a9-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b8a9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b8a9-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8a9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
