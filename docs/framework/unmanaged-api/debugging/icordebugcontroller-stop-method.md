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
ms.openlocfilehash: 3a107176e48a88a0a04534f7044c1e416caf4091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788897"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="b7639-102">ICorDebugController::Stop – metoda</span><span class="sxs-lookup"><span data-stu-id="b7639-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="b7639-103">Provede kooperativní zastavení na všech vláknech, na kterých běží spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="b7639-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7639-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7639-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7639-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7639-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="b7639-106">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="b7639-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7639-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7639-107">Remarks</span></span>  
 <span data-ttu-id="b7639-108">`Stop` provádí kooperativní zastavení na všech vláknech spouštějících spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="b7639-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="b7639-109">Během relace ladění jenom spravovaného kódu se můžou nespravované podprocesy dál spouštět (při pokusu o volání spravovaného kódu se ale zablokuje).</span><span class="sxs-lookup"><span data-stu-id="b7639-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="b7639-110">Během relace ladění spolupráce dojde také k zastavení nespravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="b7639-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="b7639-111">Hodnota `dwTimeoutIgnored` se aktuálně ignoruje a považuje se za INFINITou (-1).</span><span class="sxs-lookup"><span data-stu-id="b7639-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="b7639-112">Pokud se kooperativní zastavení nepovede kvůli zablokování, všechna vlákna se pozastaví a vrátí se E_TIMEOUT.</span><span class="sxs-lookup"><span data-stu-id="b7639-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7639-113">`Stop` je jediná synchronní metoda v rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b7639-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="b7639-114">Když `Stop` vrátí S_OK, proces se zastaví.</span><span class="sxs-lookup"><span data-stu-id="b7639-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="b7639-115">Pro upozornění naslouchacího procesu zastavení není zadáno žádné zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="b7639-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="b7639-116">Aby bylo možné pokračovat v procesu, musí ladicí program volat funkci [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b7639-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="b7639-117">Ladicí program udržuje čítač zastavení.</span><span class="sxs-lookup"><span data-stu-id="b7639-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="b7639-118">Když počítadlo dosáhne nuly, kontroler se obnoví.</span><span class="sxs-lookup"><span data-stu-id="b7639-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="b7639-119">Každé volání `Stop` nebo každé odeslané zpětné volání zvýší hodnotu čítače.</span><span class="sxs-lookup"><span data-stu-id="b7639-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="b7639-120">Každé volání `ICorDebugController::Continue` sníží čítač.</span><span class="sxs-lookup"><span data-stu-id="b7639-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7639-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7639-121">Requirements</span></span>  
 <span data-ttu-id="b7639-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7639-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7639-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7639-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7639-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b7639-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7639-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7639-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7639-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7639-126">See also</span></span>
