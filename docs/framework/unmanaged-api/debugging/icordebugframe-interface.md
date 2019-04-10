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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a15d7f16676b8b9d66f8d1ba7484f3fec5735a44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222560"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="57d2f-102">ICorDebugFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57d2f-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="57d2f-103">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="57d2f-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57d2f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57d2f-104">Methods</span></span>  
  
|<span data-ttu-id="57d2f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-105">Method</span></span>|<span data-ttu-id="57d2f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="57d2f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57d2f-107">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="57d2f-108">Získá icordebugstepper – k provádění operací krokování vzhledem k to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="57d2f-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="57d2f-109">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="57d2f-110">Získá ukazatel `ICorDebugFrame` v aktuálním řetězci, volá tento rámec, nebo vrátí hodnotu null, pokud je vnitřní rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="57d2f-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="57d2f-111">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="57d2f-112">Získá ukazatel `ICorDebugFrame` v aktuálním řetězci, který volá tento rámec nebo vrátí hodnotu null, pokud je nejkrajnější rámce v řetězci.</span><span class="sxs-lookup"><span data-stu-id="57d2f-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="57d2f-113">GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="57d2f-114">Získá ukazatel icordebugchain – to `ICorDebugFrame` je součástí.</span><span class="sxs-lookup"><span data-stu-id="57d2f-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="57d2f-115">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="57d2f-116">Získá ukazatel na ICorDebugCode přidružené k tento rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="57d2f-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="57d2f-117">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="57d2f-118">Získá ukazatel na ICorDebugFunction, která obsahuje kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="57d2f-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="57d2f-119">GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="57d2f-120">Získá token metadat pro funkci, která obsahuje kód spojený s rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="57d2f-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="57d2f-121">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="57d2f-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="57d2f-122">Získá absolutní adresu rozsahu bloku zásobníku představovaného tímto rozhraním `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="57d2f-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57d2f-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57d2f-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57d2f-124">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="57d2f-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57d2f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57d2f-125">Requirements</span></span>  
 <span data-ttu-id="57d2f-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57d2f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57d2f-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57d2f-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57d2f-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57d2f-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="57d2f-129">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="57d2f-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="57d2f-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57d2f-130">See also</span></span>

- [<span data-ttu-id="57d2f-131">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57d2f-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
