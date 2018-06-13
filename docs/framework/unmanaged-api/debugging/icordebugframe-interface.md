---
title: ICorDebugFrame Interface1
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
ms.openlocfilehash: f3d6c1a2bfd66e275b506d4465731c48cd7c6515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416628"
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="0ef0c-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="0ef0c-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="0ef0c-103">Představuje snímek aktuálního zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ef0c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0ef0c-104">Methods</span></span>  
  
|<span data-ttu-id="0ef0c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-105">Method</span></span>|<span data-ttu-id="0ef0c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0ef0c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ef0c-107">CreateStepper – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="0ef0c-108">Získá ICorDebugStepper k provádění operací taktování relativně k to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="0ef0c-109">GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="0ef0c-110">Získá odkazy `ICorDebugFrame` v řetězu aktuální volá tento rámečku, nebo vrátí hodnotu null, pokud je nejvnitřnější rámečku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="0ef0c-111">GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="0ef0c-112">Získá odkazy `ICorDebugFrame` v řetězu aktuální, který je volán tohoto rámce nebo vrátí hodnotu null, pokud je nejkrajnější rámečku v řetězci.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="0ef0c-113">GetChain – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="0ef0c-114">Získá odkazy ICorDebugChain tento `ICorDebugFrame` je součástí.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="0ef0c-115">GetCode – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="0ef0c-116">Získá ukazatel na ICorDebugCode přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0ef0c-117">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="0ef0c-118">Získá ukazatel na ICorDebugFunction, který obsahuje kód spojený s Tento rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0ef0c-119">GetFunctionToken – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="0ef0c-120">Získá metadata token pro funkce, která obsahuje kód přidružené k této rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="0ef0c-121">GetStackRange – metoda</span><span class="sxs-lookup"><span data-stu-id="0ef0c-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="0ef0c-122">Získá absolutní adresu rozsahu rámce zásobníku reprezentována to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ef0c-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ef0c-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ef0c-124">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0ef0c-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef0c-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ef0c-125">Requirements</span></span>  
 <span data-ttu-id="0ef0c-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ef0c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ef0c-127">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ef0c-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ef0c-128">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ef0c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ef0c-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ef0c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef0c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ef0c-130">See Also</span></span>  
 [<span data-ttu-id="0ef0c-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ef0c-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
