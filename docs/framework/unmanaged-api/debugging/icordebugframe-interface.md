---
title: ICorDebugFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209614"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="68098-102">ICorDebugFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68098-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="68098-103">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68098-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68098-104">Metody</span><span class="sxs-lookup"><span data-stu-id="68098-104">Methods</span></span>  
  
|<span data-ttu-id="68098-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="68098-105">Method</span></span>|<span data-ttu-id="68098-106">Popis</span><span class="sxs-lookup"><span data-stu-id="68098-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68098-107">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="68098-108">Získá ICorDebugStepper, který provede operace krokování vzhledem k tomuto `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="68098-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="68098-109">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="68098-110">Získá ukazatel na z `ICorDebugFrame` aktuálního řetězce, který tento rámec volá, nebo vrátí hodnotu null, pokud se jedná o vnitřní rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="68098-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="68098-111">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="68098-112">Získá ukazatel na `ICorDebugFrame` v aktuálním řetězci, který volal tento rámec, nebo vrátí hodnotu null, pokud se jedná o nejvzdálenější rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="68098-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="68098-113">GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="68098-114">Získá ukazatel na ICorDebugChain, `ICorDebugFrame` který je součástí.</span><span class="sxs-lookup"><span data-stu-id="68098-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="68098-115">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="68098-116">Získá ukazatel na ICorDebugCode spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68098-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="68098-117">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="68098-118">Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68098-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="68098-119">GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="68098-120">Získá token metadat pro funkci, která obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="68098-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="68098-121">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="68098-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="68098-122">Získá absolutní rozsah adres rámce zásobníku reprezentovaného tímto `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="68098-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68098-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68098-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68098-124">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="68098-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68098-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68098-125">Requirements</span></span>  
 <span data-ttu-id="68098-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68098-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68098-127">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68098-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68098-128">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="68098-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68098-129">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68098-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68098-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="68098-130">See also</span></span>

- [<span data-ttu-id="68098-131">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68098-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
