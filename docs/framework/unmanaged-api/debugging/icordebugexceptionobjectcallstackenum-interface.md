---
title: ICorDebugExceptionObjectCallStackEnum::Next – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ed6c04a46a767ed122e54df0695429cf923b8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988907"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="184dd-102">ICorDebugExceptionObjectCallStackEnum::Next – rozhraní</span><span class="sxs-lookup"><span data-stu-id="184dd-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="184dd-103">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="184dd-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="184dd-104">Toto rozhraní je podtřídou třídy icordebugenum – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="184dd-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="184dd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="184dd-105">Methods</span></span>  
  
|<span data-ttu-id="184dd-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="184dd-106">Method</span></span>|<span data-ttu-id="184dd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="184dd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="184dd-108">Icordebugexceptionobjectcallstackenum::Next –</span><span class="sxs-lookup"><span data-stu-id="184dd-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="184dd-109">Získá zadaný počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty, které obsahují informace o zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="184dd-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184dd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="184dd-110">Remarks</span></span>  
 <span data-ttu-id="184dd-111">`ICorDebugExceptionObjectCallStackEnum` Icordebugenum – rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="184dd-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="184dd-112">`ICorDebugExceptionObjectCallStackEnum` Instance se vyplní [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty voláním [icordebugexceptionobjectvalue::enumerateexceptioncallstack –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="184dd-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="184dd-113">Položka zásobníku volání v kolekci můžete vytvořit výčet voláním [icordebugexceptionobjectcallstackenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="184dd-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="184dd-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="184dd-114">Requirements</span></span>  
 <span data-ttu-id="184dd-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="184dd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="184dd-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="184dd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="184dd-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="184dd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="184dd-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184dd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184dd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="184dd-119">See also</span></span>

- [<span data-ttu-id="184dd-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="184dd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="184dd-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="184dd-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
