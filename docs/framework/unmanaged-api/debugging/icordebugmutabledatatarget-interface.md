---
title: "ICorDebugMutableDataTarget rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="620a8-102">ICorDebugMutableDataTarget rozhraní</span><span class="sxs-lookup"><span data-stu-id="620a8-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="620a8-103">Rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní pro podporu měnitelný datový cíle.</span><span class="sxs-lookup"><span data-stu-id="620a8-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="620a8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="620a8-104">Methods</span></span>  
  
|<span data-ttu-id="620a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="620a8-105">Method</span></span>|<span data-ttu-id="620a8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="620a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="620a8-107">ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="620a8-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="620a8-108">Změní stav pokračování události nezpracovaných ladění na zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="620a8-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="620a8-109">Setthreadcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="620a8-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="620a8-110">Nastaví kontext (hodnot registru) vlákna.</span><span class="sxs-lookup"><span data-stu-id="620a8-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="620a8-111">Writevirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="620a8-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="620a8-112">Zapíše paměti do adresního prostoru procesu cíl.</span><span class="sxs-lookup"><span data-stu-id="620a8-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="620a8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="620a8-113">Remarks</span></span>  
 <span data-ttu-id="620a8-114">Toto rozšíření pro [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní může být implementováno pomocí ladicích nástrojů, které chcete upravit Cílový proces (například k provedení invazivní ladění).</span><span class="sxs-lookup"><span data-stu-id="620a8-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="620a8-115">Všechny tyto metody jsou volitelné v tom smyslu, že žádné jádra na základě kontroly ladění funkce budou ztraceny není implementace tohoto rozhraní nebo selhání volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="620a8-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="620a8-116">Jakákoli chyba `HRESULT` z těchto metod rozšíří na jako `HRESULT` z volání metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="620a8-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="620a8-117">Všimněte si, že jednoho volání metody ICorDebug může mít za následek více mutací a že neexistuje žádný mechanismus pro zajištění související mutací použijí transakčně (all-or-none).</span><span class="sxs-lookup"><span data-stu-id="620a8-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="620a8-118">To znamená, že pokud mutace selže po jiné (pro stejné volání ICorDebug) proběhlo úspěšně, tento cílový proces může být ponecháno v nekonzistentním stavu a ladění stane nespolehlivou.</span><span class="sxs-lookup"><span data-stu-id="620a8-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="620a8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="620a8-119">Requirements</span></span>  
 <span data-ttu-id="620a8-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="620a8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="620a8-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="620a8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="620a8-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="620a8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="620a8-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="620a8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="620a8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="620a8-124">See Also</span></span>  
 [<span data-ttu-id="620a8-125">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="620a8-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="620a8-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="620a8-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
