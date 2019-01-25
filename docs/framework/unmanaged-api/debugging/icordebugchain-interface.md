---
title: ICorDebugChain Interface1
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
ms.openlocfilehash: e0bb716f1ad4087642a76dc84266ec6d3f46c1ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571201"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="72077-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="72077-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="72077-103">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="72077-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72077-104">Metody</span><span class="sxs-lookup"><span data-stu-id="72077-104">Methods</span></span>  
  
|<span data-ttu-id="72077-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="72077-105">Method</span></span>|<span data-ttu-id="72077-106">Popis</span><span class="sxs-lookup"><span data-stu-id="72077-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72077-107">EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="72077-108">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaného v řetězci, od posledního rámce.</span><span class="sxs-lookup"><span data-stu-id="72077-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="72077-109">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="72077-110">Získá aktivní (to znamená nejnovější) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="72077-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="72077-111">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="72077-112">Získá řetězec, který byl volán tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="72077-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="72077-113">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="72077-114">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="72077-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="72077-115">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="72077-116">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="72077-116">Not implemented.</span></span>|  
|[<span data-ttu-id="72077-117">GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="72077-118">Získá další řetězec rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="72077-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="72077-119">GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="72077-120">Získá předchozí řetězu rámce pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="72077-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="72077-121">GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="72077-122">Získá důvod genesis tento řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="72077-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="72077-123">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="72077-124">Získá do registru pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="72077-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="72077-125">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="72077-126">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="72077-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="72077-127">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="72077-128">Získá fyzické vlákno, které tento řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="72077-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="72077-129">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="72077-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="72077-130">Získá hodnotu určující, zda tento řetězec používá spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="72077-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72077-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72077-131">Remarks</span></span>  
 <span data-ttu-id="72077-132">Rámce zásobníku v řetězci zabírají prostor souvislých zásobníku a sdílejí stejný vlákna a kontext.</span><span class="sxs-lookup"><span data-stu-id="72077-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="72077-133">Řetězec může představovat buď řetězy spravovaného i nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="72077-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="72077-134">Prázdná `ICorDebugChain` instance představuje řetěz nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="72077-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72077-135">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="72077-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72077-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72077-136">Requirements</span></span>  
 <span data-ttu-id="72077-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72077-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72077-138">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72077-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72077-139">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72077-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72077-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72077-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72077-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72077-141">See also</span></span>
- [<span data-ttu-id="72077-142">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="72077-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
