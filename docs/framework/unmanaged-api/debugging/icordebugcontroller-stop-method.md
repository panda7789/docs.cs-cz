---
title: ICorDebugController::Stop – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbe0459824499aba86c908012f038256f9923513
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496680"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="52a1e-102">ICorDebugController::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="52a1e-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="52a1e-103">Provádí kooperativní stop na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="52a1e-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52a1e-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52a1e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52a1e-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="52a1e-106">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="52a1e-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52a1e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52a1e-107">Remarks</span></span>  
 <span data-ttu-id="52a1e-108">`Stop` provádí kooperativní stop na všech vláknech spuštění spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="52a1e-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="52a1e-109">Během ladicí relace pouze pro spravované, nespravované vláken může pokračovat se zrušeným (ale zablokuje při pokusu o volání spravovaného kódu).</span><span class="sxs-lookup"><span data-stu-id="52a1e-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="52a1e-110">Během interop relaci ladění se také zastaví nespravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="52a1e-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="52a1e-111">`dwTimeoutIgnored` Hodnota je aktuálně ignorována a považována jako NEKONEČNÉ (-1).</span><span class="sxs-lookup"><span data-stu-id="52a1e-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="52a1e-112">Pokud kooperativní stop nezdaří z důvodu zablokování, všechna vlákna jsou pozastavena a E_TIMEOUT se vrátí.</span><span class="sxs-lookup"><span data-stu-id="52a1e-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52a1e-113">`Stop` je jenom synchronní metoda v rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="52a1e-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="52a1e-114">Když `Stop` vrátí hodnotu S_OK, proces se zastaví.</span><span class="sxs-lookup"><span data-stu-id="52a1e-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="52a1e-115">Upozorní moduly pro naslouchání ukončení dostane bez zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="52a1e-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="52a1e-116">Ladicí program musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) povolit pokračování procesu.</span><span class="sxs-lookup"><span data-stu-id="52a1e-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="52a1e-117">Ladicí program udržuje čítač stop.</span><span class="sxs-lookup"><span data-stu-id="52a1e-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="52a1e-118">Pokud se čítač sníží na nulu, kontroleru se obnoví.</span><span class="sxs-lookup"><span data-stu-id="52a1e-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="52a1e-119">Každé volání `Stop` nebo každého odeslaného zpětného volání zvýší čítač.</span><span class="sxs-lookup"><span data-stu-id="52a1e-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="52a1e-120">Každé volání `ICorDebugController::Continue` dekrementuje čítače.</span><span class="sxs-lookup"><span data-stu-id="52a1e-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52a1e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52a1e-121">Requirements</span></span>  
 <span data-ttu-id="52a1e-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52a1e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a1e-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52a1e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52a1e-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52a1e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52a1e-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52a1e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a1e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52a1e-126">See also</span></span>

