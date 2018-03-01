---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="79bcb-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="79bcb-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="79bcb-103">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="79bcb-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79bcb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="79bcb-104">Methods</span></span>  
  
|<span data-ttu-id="79bcb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-105">Method</span></span>|<span data-ttu-id="79bcb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="79bcb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79bcb-107">EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="79bcb-108">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaných v řetězu, počínaje nejnovější rámečku.</span><span class="sxs-lookup"><span data-stu-id="79bcb-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="79bcb-109">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="79bcb-110">Získá aktivní (tedy poslední) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="79bcb-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="79bcb-111">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="79bcb-112">Získá řetězec, který byl volány tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="79bcb-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="79bcb-113">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="79bcb-114">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="79bcb-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="79bcb-115">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="79bcb-116">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="79bcb-116">Not implemented.</span></span>|  
|[<span data-ttu-id="79bcb-117">GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="79bcb-118">Získá další řetěz snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="79bcb-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="79bcb-119">GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="79bcb-120">Získá předchozí řetěz snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="79bcb-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="79bcb-121">GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="79bcb-122">Získá důvod genesis toto volání řetězu.</span><span class="sxs-lookup"><span data-stu-id="79bcb-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="79bcb-123">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="79bcb-124">Získá zaregistrovat, nastavte pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="79bcb-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="79bcb-125">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="79bcb-126">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="79bcb-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="79bcb-127">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="79bcb-128">Získá fyzické vlákno, které je tento řetězec volání součástí.</span><span class="sxs-lookup"><span data-stu-id="79bcb-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="79bcb-129">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="79bcb-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="79bcb-130">Získá hodnotu, která určuje, zda tento řetězec používá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="79bcb-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79bcb-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79bcb-131">Remarks</span></span>  
 <span data-ttu-id="79bcb-132">Rámce zásobníku v řetězu zabírají místa na souvislý zásobníku a sdílejí stejný přístup z více vláken a kontext.</span><span class="sxs-lookup"><span data-stu-id="79bcb-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="79bcb-133">Řetěz může představovat buď řetězy kód spravované nebo nespravované.</span><span class="sxs-lookup"><span data-stu-id="79bcb-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="79bcb-134">Prázdná `ICorDebugChain` instance představuje řetězec nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="79bcb-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79bcb-135">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="79bcb-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79bcb-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79bcb-136">Requirements</span></span>  
 <span data-ttu-id="79bcb-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79bcb-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79bcb-138">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79bcb-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79bcb-139">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79bcb-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79bcb-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79bcb-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79bcb-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="79bcb-141">See Also</span></span>  
 [<span data-ttu-id="79bcb-142">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="79bcb-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
