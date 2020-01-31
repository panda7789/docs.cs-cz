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
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792074"
---
# <a name="icordebugregisterset-interface"></a><span data-ttu-id="50801-102">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50801-102">ICorDebugRegisterSet Interface</span></span>
<span data-ttu-id="50801-103">Představuje sadu registrů, které jsou k dispozici v počítači, který aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="50801-103">Represents the set of registers available on the computer that is currently executing code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50801-104">Metody</span><span class="sxs-lookup"><span data-stu-id="50801-104">Methods</span></span>  
  
|<span data-ttu-id="50801-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="50801-105">Method</span></span>|<span data-ttu-id="50801-106">Popis</span><span class="sxs-lookup"><span data-stu-id="50801-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50801-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="50801-107">GetRegisters Method</span></span>](icordebugregisterset-getregisters-method.md)|<span data-ttu-id="50801-108">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="50801-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="50801-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="50801-109">GetRegistersAvailable Method</span></span>](icordebugregisterset-getregistersavailable-method.md)|<span data-ttu-id="50801-110">Načte bitovou masku, která označuje, které Registry v tomto `ICorDebugRegisterSet` jsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="50801-110">Gets a bit mask indicating which registers in this `ICorDebugRegisterSet` are currently available.</span></span>|  
|[<span data-ttu-id="50801-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="50801-111">GetThreadContext Method</span></span>](icordebugregisterset-getthreadcontext-method.md)|<span data-ttu-id="50801-112">Získá kontext aktuálního vlákna.</span><span class="sxs-lookup"><span data-stu-id="50801-112">Gets the context of the current thread.</span></span>|  
|[<span data-ttu-id="50801-113">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="50801-113">SetRegisters Method</span></span>](icordebugregisterset-setregisters-method.md)|<span data-ttu-id="50801-114">Není implementováno pro .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="50801-114">Not implemented for the .NET Framework version 2.0.</span></span>|  
|[<span data-ttu-id="50801-115">SetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="50801-115">SetThreadContext Method</span></span>](icordebugregisterset-setthreadcontext-method.md)|<span data-ttu-id="50801-116">Není implementováno pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="50801-116">Not implemented for the .NET Framework 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50801-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50801-117">Remarks</span></span>  
 <span data-ttu-id="50801-118">Rozhraní `ICorDebugRegisterSet` podporuje pouze 32 bitové Registry.</span><span class="sxs-lookup"><span data-stu-id="50801-118">The `ICorDebugRegisterSet` interface supports only 32-bit registers.</span></span> <span data-ttu-id="50801-119">Použijte rozhraní [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) na platformách, jako je IA-64, které vyžadují další registry.</span><span class="sxs-lookup"><span data-stu-id="50801-119">Use the [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) interface on platforms such as IA-64 that require additional registers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50801-120">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="50801-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50801-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50801-121">Requirements</span></span>  
 <span data-ttu-id="50801-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50801-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50801-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50801-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50801-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="50801-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50801-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50801-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50801-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50801-126">See also</span></span>

- [<span data-ttu-id="50801-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="50801-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="50801-128">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="50801-128">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
