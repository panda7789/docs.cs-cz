---
title: ICorDebugMutableDataTarget – rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 682e927388d3392d970338314f97d46c9e57e760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139339"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="0d3f8-102">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0d3f8-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="0d3f8-103">Rozšiřuje rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d3f8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0d3f8-104">Methods</span></span>  
  
|<span data-ttu-id="0d3f8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0d3f8-105">Method</span></span>|<span data-ttu-id="0d3f8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0d3f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d3f8-107">ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="0d3f8-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="0d3f8-108">Změní stav pokračování pro nedokončenou událost ladění v zadaném vlákně.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="0d3f8-109">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="0d3f8-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="0d3f8-110">Nastaví kontext (hodnoty registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="0d3f8-111">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="0d3f8-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="0d3f8-112">Zapíše paměť do cílového adresního prostoru procesu.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d3f8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d3f8-113">Remarks</span></span>  
 <span data-ttu-id="0d3f8-114">Toto rozšíření rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) může být implementováno pomocí ladicích nástrojů, které chtějí upravit cílový proces (například pro provádění živých invazivních ladění).</span><span class="sxs-lookup"><span data-stu-id="0d3f8-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="0d3f8-115">Všechny tyto metody jsou nepovinné v tom smyslu, že nedojde ke ztrátě žádné základní funkce ladění založené na kontrole tím, že neimplementuje toto rozhraní nebo nezpůsobí volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="0d3f8-116">Jakékoli selhání `HRESULT` z těchto metod bude rozšířeno jako `HRESULT` z volání metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="0d3f8-117">Všimněte si, že jedno volání metody ICorDebug může mít za následek vícenásobné mutace a že neexistuje žádný mechanismus pro zajištění souvisejících mutací, které jsou prováděny jako transakční (vše-nebo-None).</span><span class="sxs-lookup"><span data-stu-id="0d3f8-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="0d3f8-118">To znamená, že pokud po úspěšném pokusu o provedení jiné (pro stejné volání ICorDebug) dojde k chybě, cílový proces může být ponechán v nekonzistentním stavu a ladění může být nespolehlivé.</span><span class="sxs-lookup"><span data-stu-id="0d3f8-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d3f8-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d3f8-119">Requirements</span></span>  
 <span data-ttu-id="0d3f8-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d3f8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d3f8-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0d3f8-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d3f8-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0d3f8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d3f8-123">**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d3f8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d3f8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d3f8-124">See also</span></span>

- [<span data-ttu-id="0d3f8-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0d3f8-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0d3f8-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="0d3f8-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
