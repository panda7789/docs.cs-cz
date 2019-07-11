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
ms.openlocfilehash: 83bb52f7f2035605914e2fe72ce2daf78de5bc1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749913"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="aef44-102">ICorDebugController::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="aef44-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="aef44-103">Provádí kooperativní stop na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="aef44-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aef44-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aef44-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="aef44-106">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="aef44-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aef44-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aef44-107">Remarks</span></span>  
 <span data-ttu-id="aef44-108">`Stop` provádí kooperativní stop na všech vláknech spuštění spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="aef44-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="aef44-109">Během ladicí relace pouze pro spravované, nespravované vláken může pokračovat se zrušeným (ale zablokuje při pokusu o volání spravovaného kódu).</span><span class="sxs-lookup"><span data-stu-id="aef44-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="aef44-110">Během interop relaci ladění se také zastaví nespravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="aef44-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="aef44-111">`dwTimeoutIgnored` Hodnota je aktuálně ignorována a považována jako NEKONEČNÉ (-1).</span><span class="sxs-lookup"><span data-stu-id="aef44-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="aef44-112">Pokud kooperativní stop nezdaří z důvodu zablokování, všechna vlákna jsou pozastavena a E_TIMEOUT se vrátí.</span><span class="sxs-lookup"><span data-stu-id="aef44-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aef44-113">`Stop` je jenom synchronní metoda v rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="aef44-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="aef44-114">Když `Stop` vrátí hodnotu S_OK, proces se zastaví.</span><span class="sxs-lookup"><span data-stu-id="aef44-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="aef44-115">Upozorní moduly pro naslouchání ukončení dostane bez zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="aef44-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="aef44-116">Ladicí program musí volat [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) povolit pokračování procesu.</span><span class="sxs-lookup"><span data-stu-id="aef44-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="aef44-117">Ladicí program udržuje čítač stop.</span><span class="sxs-lookup"><span data-stu-id="aef44-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="aef44-118">Pokud se čítač sníží na nulu, kontroleru se obnoví.</span><span class="sxs-lookup"><span data-stu-id="aef44-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="aef44-119">Každé volání `Stop` nebo každého odeslaného zpětného volání zvýší čítač.</span><span class="sxs-lookup"><span data-stu-id="aef44-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="aef44-120">Každé volání `ICorDebugController::Continue` dekrementuje čítače.</span><span class="sxs-lookup"><span data-stu-id="aef44-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef44-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aef44-121">Requirements</span></span>  
 <span data-ttu-id="aef44-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef44-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef44-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aef44-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aef44-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aef44-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aef44-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef44-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef44-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aef44-126">See also</span></span>
