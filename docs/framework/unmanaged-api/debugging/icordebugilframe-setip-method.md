---
title: "ICorDebugILFrame::SetIP – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="29d13-102">ICorDebugILFrame::SetIP – metoda</span><span class="sxs-lookup"><span data-stu-id="29d13-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="29d13-103">Nastaví ukazatel instrukce do zadaného umístění posunu v kódu (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="29d13-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29d13-104">Syntax</span></span>  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29d13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29d13-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="29d13-106">Umístění posunu v MSIL kódu.</span><span class="sxs-lookup"><span data-stu-id="29d13-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29d13-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29d13-107">Remarks</span></span>  
 <span data-ttu-id="29d13-108">Volání `SetIP` okamžitě zneplatní všechny snímky a řetězy pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="29d13-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="29d13-109">Pokud ladicí program musí rámce informace po volání `SetIP`, je třeba provést nové trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="29d13-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="29d13-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) se pokusí uchovat rámce zásobníku v platném stavu.</span><span class="sxs-lookup"><span data-stu-id="29d13-110">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="29d13-111">Ale i pokud rámečku není v platném stavu, stále může mít problémy, třeba neinicializovaných místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="29d13-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="29d13-112">Volající zodpovídá za zajištění integrita spuštěného programu.</span><span class="sxs-lookup"><span data-stu-id="29d13-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="29d13-113">Na 64bitových platformách, nelze jej přesunout ukazatel instrukce mimo `catch` nebo `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="29d13-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="29d13-114">Pokud `SetIP` nazývá aby přesunu na 64bitové platformě, vrátí HRESULT udávající neúspěch.</span><span class="sxs-lookup"><span data-stu-id="29d13-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d13-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29d13-115">Requirements</span></span>  
 <span data-ttu-id="29d13-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29d13-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d13-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29d13-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29d13-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d13-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d13-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d13-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
