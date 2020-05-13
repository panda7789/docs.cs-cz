---
title: ICorDebugMutableDataTarget – rozhraní
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: fcf7521f8261c8f8f84c7a9a9deb4b7a7d739c6e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210004"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="fbb98-102">ICorDebugMutableDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb98-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="fbb98-103">Rozšiřuje rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) pro podporu proměnlivých datových cílů.</span><span class="sxs-lookup"><span data-stu-id="fbb98-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fbb98-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fbb98-104">Methods</span></span>  
  
|<span data-ttu-id="fbb98-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fbb98-105">Method</span></span>|<span data-ttu-id="fbb98-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fbb98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fbb98-107">ContinueStatusChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb98-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="fbb98-108">Změní stav pokračování pro nedokončenou událost ladění v zadaném vlákně.</span><span class="sxs-lookup"><span data-stu-id="fbb98-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="fbb98-109">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb98-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="fbb98-110">Nastaví kontext (hodnoty registru) pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="fbb98-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="fbb98-111">WriteVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="fbb98-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="fbb98-112">Zapíše paměť do cílového adresního prostoru procesu.</span><span class="sxs-lookup"><span data-stu-id="fbb98-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbb98-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fbb98-113">Remarks</span></span>  
 <span data-ttu-id="fbb98-114">Toto rozšíření rozhraní [ICorDebugDataTarget](icordebugdatatarget-interface.md) může být implementováno pomocí ladicích nástrojů, které chtějí upravit cílový proces (například pro provádění živých invazivních ladění).</span><span class="sxs-lookup"><span data-stu-id="fbb98-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="fbb98-115">Všechny tyto metody jsou nepovinné v tom smyslu, že nedojde ke ztrátě žádné základní funkce ladění založené na kontrole tím, že neimplementuje toto rozhraní nebo nezpůsobí volání těchto metod.</span><span class="sxs-lookup"><span data-stu-id="fbb98-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="fbb98-116">Jakékoli selhání `HRESULT` z těchto metod bude rozšířeno jako `HRESULT` z volání metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="fbb98-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="fbb98-117">Všimněte si, že jedno volání metody ICorDebug může mít za následek vícenásobné mutace a že neexistuje žádný mechanismus pro zajištění souvisejících mutací, které jsou prováděny jako transakční (vše-nebo-None).</span><span class="sxs-lookup"><span data-stu-id="fbb98-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="fbb98-118">To znamená, že pokud po úspěšném pokusu o provedení jiné (pro stejné volání ICorDebug) dojde k chybě, cílový proces může být ponechán v nekonzistentním stavu a ladění může být nespolehlivé.</span><span class="sxs-lookup"><span data-stu-id="fbb98-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb98-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fbb98-119">Requirements</span></span>  
 <span data-ttu-id="fbb98-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb98-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb98-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fbb98-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbb98-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fbb98-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbb98-123">**Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbb98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb98-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbb98-124">See also</span></span>

- [<span data-ttu-id="fbb98-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbb98-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fbb98-126">Ladění</span><span class="sxs-lookup"><span data-stu-id="fbb98-126">Debugging</span></span>](index.md)
