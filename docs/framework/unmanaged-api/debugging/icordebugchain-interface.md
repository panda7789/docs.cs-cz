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
ms.openlocfilehash: 6ae0fec0f8de2bbe3862f9f70ed9cf3d32af34c4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894214"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="7fee4-102">ICorDebugChain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fee4-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="7fee4-103">Představuje segment fyzického nebo logického zásobníku volání.</span><span class="sxs-lookup"><span data-stu-id="7fee4-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fee4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7fee4-104">Methods</span></span>  
  
|<span data-ttu-id="7fee4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-105">Method</span></span>|<span data-ttu-id="7fee4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7fee4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fee4-107">EnumerateFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="7fee4-108">Získá enumerátor, který obsahuje všechny spravované rámce zásobníku v řetězci počínaje posledním rámcem.</span><span class="sxs-lookup"><span data-stu-id="7fee4-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="7fee4-109">GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="7fee4-110">Získá aktivní (tj. poslední) rámec v řetězu.</span><span class="sxs-lookup"><span data-stu-id="7fee4-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="7fee4-111">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="7fee4-112">Získá řetězec, který byl volán tímto řetězem.</span><span class="sxs-lookup"><span data-stu-id="7fee4-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="7fee4-113">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="7fee4-114">Získá řetězec, který se nazývá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="7fee4-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="7fee4-115">GetContext – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="7fee4-116">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="7fee4-116">Not implemented.</span></span>|  
|[<span data-ttu-id="7fee4-117">GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="7fee4-118">Získá další řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7fee4-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="7fee4-119">GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="7fee4-120">Načte předchozí řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7fee4-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="7fee4-121">GetReason – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="7fee4-122">Získá důvod pro Genesis tohoto volajícího řetězu.</span><span class="sxs-lookup"><span data-stu-id="7fee4-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="7fee4-123">GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="7fee4-124">Načte sadu registrů pro aktivní část tohoto řetězu.</span><span class="sxs-lookup"><span data-stu-id="7fee4-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="7fee4-125">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="7fee4-126">Získá rozsah adres segmentu zásobníku pro tento řetěz.</span><span class="sxs-lookup"><span data-stu-id="7fee4-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="7fee4-127">GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="7fee4-128">Získá fyzické vlákno, na kterém je tento řetěz volání součástí.</span><span class="sxs-lookup"><span data-stu-id="7fee4-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="7fee4-129">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="7fee4-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="7fee4-130">Získá hodnotu, která označuje, zda je v tomto řetězci spuštěn spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="7fee4-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fee4-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fee4-131">Remarks</span></span>  
 <span data-ttu-id="7fee4-132">Rámce zásobníku v řetězu zabírají souvislý prostor zásobníku a sdílejí stejné vlákno a kontext.</span><span class="sxs-lookup"><span data-stu-id="7fee4-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="7fee4-133">Řetěz může představovat buď spravované nebo nespravované řetězy kódu.</span><span class="sxs-lookup"><span data-stu-id="7fee4-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="7fee4-134">Prázdná `ICorDebugChain` instance reprezentuje řetězec nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7fee4-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fee4-135">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7fee4-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fee4-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fee4-136">Requirements</span></span>  
 <span data-ttu-id="7fee4-137">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fee4-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fee4-138">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7fee4-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fee4-139">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7fee4-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fee4-140">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fee4-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fee4-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fee4-141">See also</span></span>

- [<span data-ttu-id="7fee4-142">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fee4-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
