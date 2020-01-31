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
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790948"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="93a65-102">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93a65-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="93a65-103">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="93a65-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93a65-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93a65-104">Methods</span></span>  
  
|<span data-ttu-id="93a65-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93a65-105">Method</span></span>|<span data-ttu-id="93a65-106">Popis</span><span class="sxs-lookup"><span data-stu-id="93a65-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93a65-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="93a65-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="93a65-108">Získá zadaný počet instancí [ICorDebugVariableHome](icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="93a65-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93a65-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93a65-109">Remarks</span></span>  
 <span data-ttu-id="93a65-110">Rozhraní `ICorDebugVariableHomeEnum` implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="93a65-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="93a65-111">Instance `ICorDebugVariableHomeEnum` se naplní instancemi [ICorDebugVariableHome](icordebugvariablehome-interface.md) voláním metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93a65-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="93a65-112">Každá instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci představuje místní proměnnou nebo argument ve funkci.</span><span class="sxs-lookup"><span data-stu-id="93a65-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="93a65-113">Objekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci lze vyčíslit voláním metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93a65-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a65-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93a65-114">Requirements</span></span>  
 <span data-ttu-id="93a65-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a65-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a65-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93a65-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a65-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93a65-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a65-118">**Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a65-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a65-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93a65-119">See also</span></span>

- [<span data-ttu-id="93a65-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93a65-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="93a65-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="93a65-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
