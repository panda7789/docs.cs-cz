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
ms.openlocfilehash: 8db70faf418bc89a4543845890f65e4859d507e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592598"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="50e44-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50e44-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="50e44-103">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="50e44-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50e44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="50e44-104">Methods</span></span>  
  
|<span data-ttu-id="50e44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-105">Method</span></span>|<span data-ttu-id="50e44-106">Popis</span><span class="sxs-lookup"><span data-stu-id="50e44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50e44-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|<span data-ttu-id="50e44-108">Získá hodnotu každý registr (na počítači, který aktuálně spouští kód), která je určená bitová maska.</span><span class="sxs-lookup"><span data-stu-id="50e44-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="50e44-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="50e44-110">Získá o něco maskování určující, který registruje v tomto `ICorDebugRegisterSet` jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="50e44-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="50e44-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="50e44-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="50e44-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="50e44-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-113">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|<span data-ttu-id="50e44-114">Není implementováno pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="50e44-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="50e44-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="50e44-115">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="50e44-116">Není implementováno pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="50e44-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e44-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50e44-117">Remarks</span></span>  
 <span data-ttu-id="50e44-118">`ICorDebugRegisterSet` Rozhraní podporuje pouze 32bitové registrů.</span><span class="sxs-lookup"><span data-stu-id="50e44-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="50e44-119">Použití [icordebugregisterset2 –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) rozhraní na platformách, například IA-64, které vyžadují další registry.</span><span class="sxs-lookup"><span data-stu-id="50e44-119">Use the [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e44-120">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="50e44-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e44-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50e44-121">Requirements</span></span>  
 <span data-ttu-id="50e44-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50e44-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e44-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50e44-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50e44-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e44-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e44-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e44-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e44-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50e44-126">See also</span></span>
- [<span data-ttu-id="50e44-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="50e44-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="50e44-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50e44-128">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
