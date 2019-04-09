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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126201"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="97386-102">ICorDebugExceptionObjectCallStackEnum::Next – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97386-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="97386-103">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="97386-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="97386-104">Toto rozhraní je podtřídou třídy icordebugenum – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="97386-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97386-105">Metody</span><span class="sxs-lookup"><span data-stu-id="97386-105">Methods</span></span>  
  
|<span data-ttu-id="97386-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="97386-106">Method</span></span>|<span data-ttu-id="97386-107">Popis</span><span class="sxs-lookup"><span data-stu-id="97386-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97386-108">Icordebugexceptionobjectcallstackenum::Next –</span><span class="sxs-lookup"><span data-stu-id="97386-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="97386-109">Získá zadaný počet [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty, které obsahují informace o zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="97386-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97386-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97386-110">Remarks</span></span>  
 <span data-ttu-id="97386-111">`ICorDebugExceptionObjectCallStackEnum` Icordebugenum – rozhraní implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="97386-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="97386-112">`ICorDebugExceptionObjectCallStackEnum` Instance se vyplní [cordebugexceptionobjectstackframe –](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objekty voláním [icordebugexceptionobjectvalue::enumerateexceptioncallstack –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="97386-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="97386-113">Položka zásobníku volání v kolekci můžete vytvořit výčet voláním [icordebugexceptionobjectcallstackenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) – metoda</span><span class="sxs-lookup"><span data-stu-id="97386-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97386-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97386-114">Requirements</span></span>  
 <span data-ttu-id="97386-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97386-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97386-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97386-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97386-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97386-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="97386-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="97386-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97386-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97386-119">See also</span></span>

- [<span data-ttu-id="97386-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97386-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="97386-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="97386-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
