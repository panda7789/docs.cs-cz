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
ms.openlocfilehash: a9b65449747fde42f9cd770e33741ef34d33fbb8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121025"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="b0dde-102">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0dde-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="b0dde-103">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b0dde-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0dde-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0dde-104">Methods</span></span>  
  
|<span data-ttu-id="b0dde-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0dde-105">Method</span></span>|<span data-ttu-id="b0dde-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b0dde-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0dde-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b0dde-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="b0dde-108">Získá zadaný počet instancí [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b0dde-108">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0dde-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0dde-109">Remarks</span></span>  
 <span data-ttu-id="b0dde-110">Rozhraní `ICorDebugVariableHomeEnum` implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="b0dde-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="b0dde-111">Instance `ICorDebugVariableHomeEnum` se naplní instancemi [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) voláním metody [ICorDebugCode4:: EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b0dde-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="b0dde-112">Každá instance [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) v kolekci představuje místní proměnnou nebo argument ve funkci.</span><span class="sxs-lookup"><span data-stu-id="b0dde-112">Each [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="b0dde-113">Objekty [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) v kolekci lze vyčíslit voláním metody [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b0dde-113">The  [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0dde-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0dde-114">Requirements</span></span>  
 <span data-ttu-id="b0dde-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0dde-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0dde-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0dde-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0dde-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0dde-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0dde-118">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0dde-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0dde-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0dde-119">See also</span></span>

- [<span data-ttu-id="b0dde-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0dde-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="b0dde-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b0dde-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
