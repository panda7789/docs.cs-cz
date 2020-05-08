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
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975989"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="16c4d-102">ICorDebugExceptionObjectCallStackEnum::Next – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16c4d-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="16c4d-103">Poskytuje enumerátor pro informace zásobníku volání, který je vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="16c4d-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="16c4d-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="16c4d-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16c4d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="16c4d-105">Methods</span></span>  
  
|<span data-ttu-id="16c4d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="16c4d-106">Method</span></span>|<span data-ttu-id="16c4d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="16c4d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16c4d-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="16c4d-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="16c4d-109">Získá zadaný počet objektů [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) , které obsahují informace o zásobníku volání objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="16c4d-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16c4d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16c4d-110">Remarks</span></span>  
 <span data-ttu-id="16c4d-111">`ICorDebugExceptionObjectCallStackEnum` Rozhraní implementuje rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="16c4d-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="16c4d-112">Instance je naplněna objekty [CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) voláním metody [ICorDebugExceptionObjectValue –:: EnumerateExceptionCallStack –.](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) `ICorDebugExceptionObjectCallStackEnum`</span><span class="sxs-lookup"><span data-stu-id="16c4d-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="16c4d-113">Položky zásobníku volání v kolekci lze vyčíslit voláním metody [ICorDebugExceptionObjectCallStackEnum:: Next.](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="16c4d-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c4d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="16c4d-114">Requirements</span></span>  
 <span data-ttu-id="16c4d-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c4d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c4d-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16c4d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c4d-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="16c4d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c4d-118">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c4d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c4d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="16c4d-119">See also</span></span>

- [<span data-ttu-id="16c4d-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="16c4d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="16c4d-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="16c4d-121">Debugging</span></span>](index.md)
