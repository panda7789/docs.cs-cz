---
title: ICorDebugMutableDataTarget – rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8b33b07e7c9f83f5874dea1455cd70dcc3206de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105934"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="45e31-102">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45e31-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="45e31-103">Rozšiřuje [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu proměnlivé datové cíle.</span><span class="sxs-lookup"><span data-stu-id="45e31-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45e31-104">Metody</span><span class="sxs-lookup"><span data-stu-id="45e31-104">Methods</span></span>  
  
|<span data-ttu-id="45e31-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="45e31-105">Method</span></span>|<span data-ttu-id="45e31-106">Popis</span><span class="sxs-lookup"><span data-stu-id="45e31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45e31-107">ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="45e31-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="45e31-108">Změní stav pokračování pro zbývající ladění události u zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="45e31-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="45e31-109">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="45e31-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="45e31-110">Nastaví kontext (hodnot registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="45e31-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="45e31-111">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="45e31-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="45e31-112">Zapíše paměti do adresového prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="45e31-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e31-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45e31-113">Remarks</span></span>  
 <span data-ttu-id="45e31-114">Toto rozšíření [icordebugdatatarget –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní může být implementována ladicí nástroje, které chcete upravit Cílový proces (například k provádění invazivní ladění).</span><span class="sxs-lookup"><span data-stu-id="45e31-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="45e31-115">Všechny tyto metody jsou volitelné v tom smyslu, že žádná základní na základě kontroly ladění funkce je ztraceny bez implementace tohoto rozhraní nebo selhání volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="45e31-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="45e31-116">Jakékoli neúspěchy `HRESULT` z těchto metod bude šířit jako `HRESULT` z volání metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="45e31-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="45e31-117">Mějte na paměti, že jedním voláním metody ICorDebug může vést k více mutace a že neexistuje žádný mechanismus pro zajištění související mutace použijí transakčně (all-or-none).</span><span class="sxs-lookup"><span data-stu-id="45e31-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="45e31-118">To znamená, že pokud mutaci selže po jiné (pro stejné volání ICorDebug) byly úspěšné, Cílový proces se může stát zůstane v nekonzistentním stavu a ladění může být nespolehlivá.</span><span class="sxs-lookup"><span data-stu-id="45e31-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45e31-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45e31-119">Requirements</span></span>  
 <span data-ttu-id="45e31-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45e31-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e31-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45e31-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45e31-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45e31-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45e31-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e31-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e31-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45e31-124">See also</span></span>

- [<span data-ttu-id="45e31-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="45e31-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="45e31-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="45e31-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
