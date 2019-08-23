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
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936996"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="aac03-102">ICorDebugFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aac03-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="aac03-103">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aac03-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aac03-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aac03-104">Methods</span></span>  
  
|<span data-ttu-id="aac03-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-105">Method</span></span>|<span data-ttu-id="aac03-106">Popis</span><span class="sxs-lookup"><span data-stu-id="aac03-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aac03-107">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="aac03-108">Získá ICorDebugStepper, který provede operace krokování vzhledem k `ICorDebugFrame`tomuto.</span><span class="sxs-lookup"><span data-stu-id="aac03-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="aac03-109">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="aac03-110">Získá ukazatel na `ICorDebugFrame` z aktuálního řetězce, který tento rámec volá, nebo vrátí hodnotu null, pokud se jedná o vnitřní rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="aac03-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="aac03-111">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="aac03-112">Získá ukazatel na `ICorDebugFrame` v aktuálním řetězci, který volal tento rámec, nebo vrátí hodnotu null, pokud se jedná o nejvzdálenější rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="aac03-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="aac03-113">GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="aac03-114">Získá ukazatel na ICorDebugChain `ICorDebugFrame` , který je součástí.</span><span class="sxs-lookup"><span data-stu-id="aac03-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="aac03-115">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="aac03-116">Získá ukazatel na ICorDebugCode spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aac03-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="aac03-117">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="aac03-118">Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aac03-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="aac03-119">GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="aac03-120">Získá token metadat pro funkci, která obsahuje kód spojený s tímto rámcem zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aac03-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="aac03-121">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="aac03-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="aac03-122">Získá absolutní rozsah adres rámce zásobníku reprezentovaného tímto `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="aac03-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aac03-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aac03-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aac03-124">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="aac03-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac03-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aac03-125">Requirements</span></span>  
 <span data-ttu-id="aac03-126">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aac03-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac03-127">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aac03-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aac03-128">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aac03-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aac03-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac03-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac03-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aac03-130">See also</span></span>

- [<span data-ttu-id="aac03-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aac03-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
