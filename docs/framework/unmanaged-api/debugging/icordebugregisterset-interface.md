---
title: ICorDebugRegisterSet – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4b28d60b3a1da32d2d9db84aa92ca4c9bf769aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423192"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="c4838-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4838-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="c4838-103">Představuje sadu registrů, k dispozici v počítači, který je aktuálně provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="c4838-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4838-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c4838-104">Methods</span></span>  
  
|<span data-ttu-id="c4838-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-105">Method</span></span>|<span data-ttu-id="c4838-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c4838-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4838-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="c4838-108">Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.</span><span class="sxs-lookup"><span data-stu-id="c4838-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="c4838-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="c4838-110">Získá trochu maskování, která určuje, který registruje v tomto `ICorDebugRegisterSet` jsou nyní k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c4838-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="c4838-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="c4838-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="c4838-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="c4838-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="c4838-114">Není implementována pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4838-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="c4838-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c4838-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="c4838-116">Není implementována pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4838-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4838-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4838-117">Remarks</span></span>  
 <span data-ttu-id="c4838-118">`ICorDebugRegisterSet` Rozhraní podporuje pouze 32bitové registry.</span><span class="sxs-lookup"><span data-stu-id="c4838-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="c4838-119">Použití [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) rozhraní na platformách, které vyžadují další registrů, například IA-64.</span><span class="sxs-lookup"><span data-stu-id="c4838-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4838-120">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4838-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4838-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4838-121">Requirements</span></span>  
 <span data-ttu-id="c4838-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4838-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4838-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4838-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4838-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4838-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4838-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4838-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4838-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4838-126">See Also</span></span>  
 [<span data-ttu-id="c4838-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4838-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c4838-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4838-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
