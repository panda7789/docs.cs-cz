---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f964b5390e601b518acad44dd6fd170399ff0af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="3e642-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="3e642-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="3e642-103">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="3e642-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e642-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3e642-104">Methods</span></span>  
  
|<span data-ttu-id="3e642-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-105">Method</span></span>|<span data-ttu-id="3e642-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3e642-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e642-107">Enumerateframes – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="3e642-108">Získá enumerátor, který obsahuje všechny rámce zásobníku spravovaných v řetězu, počínaje nejnovější rámečku.</span><span class="sxs-lookup"><span data-stu-id="3e642-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="3e642-109">Getactiveframe – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="3e642-110">Získá aktivní (tedy poslední) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="3e642-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="3e642-111">Getcallee – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="3e642-112">Získá řetězec, který byl volány tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e642-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="3e642-113">Getcaller – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="3e642-114">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e642-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="3e642-115">Getcontext – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="3e642-116">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="3e642-116">Not implemented.</span></span>|  
|[<span data-ttu-id="3e642-117">GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="3e642-118">Získá další řetěz snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="3e642-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="3e642-119">Getprevious – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="3e642-120">Získá předchozí řetěz snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="3e642-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="3e642-121">Getreason – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="3e642-122">Získá důvod genesis toto volání řetězu.</span><span class="sxs-lookup"><span data-stu-id="3e642-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="3e642-123">Getregisterset – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="3e642-124">Získá zaregistrovat, nastavte pro aktivní součástí tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e642-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="3e642-125">Getstackrange – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="3e642-126">Získá rozsah adres segmentu zásobníku pro tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e642-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="3e642-127">Getthread – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="3e642-128">Získá fyzické vlákno, které je tento řetězec volání součástí.</span><span class="sxs-lookup"><span data-stu-id="3e642-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="3e642-129">Ismanaged – metoda</span><span class="sxs-lookup"><span data-stu-id="3e642-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="3e642-130">Získá hodnotu, která určuje, zda tento řetězec používá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3e642-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e642-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e642-131">Remarks</span></span>  
 <span data-ttu-id="3e642-132">Rámce zásobníku v řetězu zabírají místa na souvislý zásobníku a sdílejí stejný přístup z více vláken a kontext.</span><span class="sxs-lookup"><span data-stu-id="3e642-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="3e642-133">Řetěz může představovat buď řetězy kód spravované nebo nespravované.</span><span class="sxs-lookup"><span data-stu-id="3e642-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="3e642-134">Prázdná `ICorDebugChain` instance představuje řetězec nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3e642-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e642-135">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3e642-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e642-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e642-136">Requirements</span></span>  
 <span data-ttu-id="3e642-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e642-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e642-138">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e642-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e642-139">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e642-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e642-140">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e642-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e642-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e642-141">See Also</span></span>  
 [<span data-ttu-id="3e642-142">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e642-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
