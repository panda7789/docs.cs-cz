---
title: "ICorDebugVariableHomeEnum rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum
helpviewer_keywords: ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e64a52ca70606f83138b636f7ccb62ba18908f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="a1289-102">ICorDebugVariableHomeEnum rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1289-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="a1289-103">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="a1289-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1289-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1289-104">Methods</span></span>  
  
|<span data-ttu-id="a1289-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1289-105">Method</span></span>|<span data-ttu-id="a1289-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1289-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1289-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a1289-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="a1289-108">Získá zadaný počet [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instancí, které obsahují informace o místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="a1289-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1289-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1289-109">Remarks</span></span>  
 <span data-ttu-id="a1289-110">`ICorDebugVariableHomeEnum` Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a1289-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="a1289-111">`ICorDebugVariableHomeEnum` Se zobrazí v instanci [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance voláním [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a1289-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="a1289-112">Každý [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance v kolekci představuje místní proměnné nebo argumentem funkcí.</span><span class="sxs-lookup"><span data-stu-id="a1289-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="a1289-113">[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) voláním mohou být uvedené v kolekci objektů [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a1289-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1289-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1289-114">Requirements</span></span>  
 <span data-ttu-id="a1289-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1289-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1289-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1289-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1289-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1289-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1289-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1289-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1289-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1289-119">See Also</span></span>  
 [<span data-ttu-id="a1289-120">ICorDebugVariableHome rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1289-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="a1289-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1289-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
