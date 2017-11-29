---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2acc825f6592eae80f67e7614ca45f175b6756d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="dc7ee-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="dc7ee-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="dc7ee-103">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc7ee-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dc7ee-104">Methods</span></span>  
  
|<span data-ttu-id="dc7ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-105">Method</span></span>|<span data-ttu-id="dc7ee-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dc7ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc7ee-107">Createstepper – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="dc7ee-108">Získá ICorDebugStepper k provádění operací taktování relativně k to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="dc7ee-109">Getcallee – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="dc7ee-110">Získá odkazy `ICorDebugFrame` v řetězu aktuální volá tento rámečku, nebo vrátí hodnotu null, pokud je nejvnitřnější rámečku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="dc7ee-111">Getcaller – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="dc7ee-112">Získá odkazy `ICorDebugFrame` v řetězu aktuální, který je volán tohoto rámce nebo vrátí hodnotu null, pokud je nejkrajnější rámečku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="dc7ee-113">Getchain – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="dc7ee-114">Získá odkazy ICorDebugChain tento `ICorDebugFrame` je součástí.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="dc7ee-115">Getcode – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="dc7ee-116">Získá ukazatel na ICorDebugCode přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="dc7ee-117">Getfunction – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="dc7ee-118">Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s Tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="dc7ee-119">Getfunctiontoken – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="dc7ee-120">Získá metadata token pro funkce, která obsahuje kód přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="dc7ee-121">Getstackrange – metoda</span><span class="sxs-lookup"><span data-stu-id="dc7ee-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="dc7ee-122">Získá absolutní adresu rozsahu rámce zásobníku reprezentována to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc7ee-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc7ee-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc7ee-124">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="dc7ee-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc7ee-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc7ee-125">Requirements</span></span>  
 <span data-ttu-id="dc7ee-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc7ee-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc7ee-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc7ee-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc7ee-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc7ee-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc7ee-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc7ee-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc7ee-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc7ee-130">See Also</span></span>  
 [<span data-ttu-id="dc7ee-131">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc7ee-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
