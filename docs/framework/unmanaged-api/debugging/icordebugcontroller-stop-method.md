---
title: "ICorDebugController::Stop – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a8699a54814b37cc03404b72330812f3eb2b2f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="14bd4-102">ICorDebugController::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="14bd4-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="14bd4-103">Provede spolupráci zastavení všech vláken, které jsou spuštěny spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="14bd4-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14bd4-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14bd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14bd4-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="14bd4-106">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="14bd4-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14bd4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14bd4-107">Remarks</span></span>  
 <span data-ttu-id="14bd4-108">`Stop`provede spolupráci zastavení na všechna vlákna systémem spravované kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="14bd4-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="14bd4-109">Během ladicí relace pouze pro spravované, nespravované vláken nadále spustit (ale zablokuje při pokusu o volání spravovaný kód).</span><span class="sxs-lookup"><span data-stu-id="14bd4-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="14bd4-110">Během zprostředkovatel komunikace s objekty ladicí relace bude také zastavena nespravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="14bd4-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="14bd4-111">`dwTimeoutIgnored` Hodnota je aktuálně ignorován a považován za NEKONEČNÉ (-1).</span><span class="sxs-lookup"><span data-stu-id="14bd4-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="14bd4-112">Pokud spolupráci zastavení nezdaří z důvodu zablokování, jsou pozastavena všechna vlákna a je vrácen E_TIMEOUT.</span><span class="sxs-lookup"><span data-stu-id="14bd4-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14bd4-113">`Stop`je pouze synchronní metoda v rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="14bd4-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="14bd4-114">Když `Stop` vrátí S_OK, proces se zastaví.</span><span class="sxs-lookup"><span data-stu-id="14bd4-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="14bd4-115">Bez zpětného volání dostane oznámení naslouchací procesy tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="14bd4-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="14bd4-116">Ladicí program musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) povolit pokračování procesu.</span><span class="sxs-lookup"><span data-stu-id="14bd4-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="14bd4-117">Ladicí program udržuje čítač zastavit.</span><span class="sxs-lookup"><span data-stu-id="14bd4-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="14bd4-118">Pokud čítač přejde na hodnotu nula, je obnoven běh kontroleru.</span><span class="sxs-lookup"><span data-stu-id="14bd4-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="14bd4-119">Každé volání `Stop` nebo každý odeslat zpětné volání zvýší čítače.</span><span class="sxs-lookup"><span data-stu-id="14bd4-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="14bd4-120">Každé volání `ICorDebugController::Continue` snížení hodnoty čítače.</span><span class="sxs-lookup"><span data-stu-id="14bd4-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14bd4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14bd4-121">Requirements</span></span>  
 <span data-ttu-id="14bd4-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bd4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14bd4-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14bd4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14bd4-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14bd4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14bd4-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14bd4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bd4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="14bd4-126">See Also</span></span>  
 
