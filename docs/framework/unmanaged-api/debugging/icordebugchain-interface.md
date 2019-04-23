---
title: ICorDebugChain – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01dded47fca26df11781153eb45693057a25ad01
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220705"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="add43-102">ICorDebugChain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="add43-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="add43-103">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="add43-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="add43-104">Metody</span><span class="sxs-lookup"><span data-stu-id="add43-104">Methods</span></span>  
  
|<span data-ttu-id="add43-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="add43-105">Method</span></span>|<span data-ttu-id="add43-106">Popis</span><span class="sxs-lookup"><span data-stu-id="add43-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="add43-107">EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="add43-108">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaného v řetězci, od posledního rámce.</span><span class="sxs-lookup"><span data-stu-id="add43-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="add43-109">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="add43-110">Získá aktivní (to znamená nejnovější) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="add43-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="add43-111">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="add43-112">Získá řetězec, který byl volán tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="add43-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="add43-113">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="add43-114">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="add43-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="add43-115">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="add43-116">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="add43-116">Not implemented.</span></span>|  
|[<span data-ttu-id="add43-117">GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="add43-118">Získá další řetězec rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="add43-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="add43-119">GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="add43-120">Získá předchozí řetězu rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="add43-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="add43-121">GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="add43-122">Získá důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="add43-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="add43-123">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="add43-124">Získá do registru pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="add43-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="add43-125">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="add43-126">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="add43-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="add43-127">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="add43-128">Získá fyzické vlákno, které tento řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="add43-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="add43-129">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="add43-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="add43-130">Získá hodnotu určující, zda tento řetězec používá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="add43-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="add43-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="add43-131">Remarks</span></span>  
 <span data-ttu-id="add43-132">Rámce zásobníku v řetězci zabírají prostor souvislých zásobníku a sdílejí stejný vlákna a kontext.</span><span class="sxs-lookup"><span data-stu-id="add43-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="add43-133">Řetězec může představovat buď řetězy spravovaného i nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="add43-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="add43-134">Prázdná `ICorDebugChain` instance představuje řetěz nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="add43-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="add43-135">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="add43-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add43-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="add43-136">Requirements</span></span>  
 <span data-ttu-id="add43-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="add43-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add43-138">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="add43-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="add43-139">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="add43-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="add43-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add43-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add43-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="add43-141">See also</span></span>

- [<span data-ttu-id="add43-142">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="add43-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
