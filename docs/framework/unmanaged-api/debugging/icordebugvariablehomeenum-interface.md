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
ms.openlocfilehash: d5962de8cc2762f6ecf4864c5255da0fe83918e4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396535"
---
# <a name="icordebugvariablehomeenum-interface"></a><span data-ttu-id="1b1d0-102">ICorDebugVariableHomeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1d0-102">ICorDebugVariableHomeEnum Interface</span></span>
<span data-ttu-id="1b1d0-103">Poskytuje enumerátor pro místní proměnné a argumenty ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1b1d0-103">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b1d0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b1d0-104">Methods</span></span>  
  
|<span data-ttu-id="1b1d0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b1d0-105">Method</span></span>|<span data-ttu-id="1b1d0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1b1d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b1d0-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1d0-107">Next Method</span></span>](icordebugvariablehomeenum-next-method.md)|<span data-ttu-id="1b1d0-108">Získá zadaný počet instancí [ICorDebugVariableHome](icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1b1d0-108">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b1d0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b1d0-109">Remarks</span></span>  
 <span data-ttu-id="1b1d0-110">`ICorDebugVariableHomeEnum`Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="1b1d0-110">The `ICorDebugVariableHomeEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="1b1d0-111">`ICorDebugVariableHomeEnum`Instance je naplněná instancemi [ICorDebugVariableHome](icordebugvariablehome-interface.md) voláním metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1b1d0-111">An `ICorDebugVariableHomeEnum` instance is populated with [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances by calling the [ICorDebugCode4::EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) method.</span></span> <span data-ttu-id="1b1d0-112">Každá instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci představuje místní proměnnou nebo argument ve funkci.</span><span class="sxs-lookup"><span data-stu-id="1b1d0-112">Each [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance in the collection represents a local variable or argument in a function.</span></span> <span data-ttu-id="1b1d0-113">Objekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) v kolekci lze vyčíslit voláním metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1b1d0-113">The  [ICorDebugVariableHome](icordebugvariablehome-interface.md) objects in the collection can be enumerated by calling the [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b1d0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b1d0-114">Requirements</span></span>  
 <span data-ttu-id="1b1d0-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1d0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1d0-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1b1d0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b1d0-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1b1d0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b1d0-118">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1d0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1d0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b1d0-119">See also</span></span>

- [<span data-ttu-id="1b1d0-120">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1d0-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="1b1d0-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1d0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
