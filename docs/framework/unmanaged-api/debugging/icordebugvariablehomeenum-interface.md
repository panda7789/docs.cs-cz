---
title: ICorDebugVariableHomeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e67e4685320f56a4a6a8be2e3eb2e6c8065ce59
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080381"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="2a0ad-102">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a0ad-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="2a0ad-103">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a0ad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2a0ad-104">Methods</span></span>  
  
|<span data-ttu-id="2a0ad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2a0ad-105">Method</span></span>|<span data-ttu-id="2a0ad-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2a0ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a0ad-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2a0ad-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="2a0ad-108">Získá zadaný počet [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o lokálních proměnných a argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a0ad-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a0ad-109">Remarks</span></span>  
 <span data-ttu-id="2a0ad-110">`ICorDebugVariableHomeEnum` Icordebugenum – rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="2a0ad-111">`ICorDebugVariableHomeEnum` Instance se vyplní [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance voláním [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="2a0ad-112">Každý [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance v kolekci představují lokální proměnné nebo argumentu ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="2a0ad-113">[Icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objektů v kolekci můžete vytvořit výčet voláním [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2a0ad-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0ad-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2a0ad-114">Requirements</span></span>  
 <span data-ttu-id="2a0ad-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a0ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a0ad-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a0ad-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a0ad-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a0ad-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a0ad-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a0ad-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0ad-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a0ad-119">See also</span></span>

- [<span data-ttu-id="2a0ad-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a0ad-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="2a0ad-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2a0ad-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
