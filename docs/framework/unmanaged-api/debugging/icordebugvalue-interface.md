---
title: ICorDebugValue – rozhraní 1
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41afc2e4305034340ad408e52ce08372bf8962dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507444"
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="eba1a-102">ICorDebugValue – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="eba1a-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="eba1a-103">Reprezentuje hodnotu v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="eba1a-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="eba1a-104">Hodnota může být čtení nebo zápis hodnoty.</span><span class="sxs-lookup"><span data-stu-id="eba1a-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eba1a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="eba1a-105">Methods</span></span>  
  
|<span data-ttu-id="eba1a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="eba1a-106">Method</span></span>|<span data-ttu-id="eba1a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="eba1a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eba1a-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="eba1a-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="eba1a-109">Tato metoda teď není implementovaná.</span><span class="sxs-lookup"><span data-stu-id="eba1a-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="eba1a-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="eba1a-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="eba1a-111">Získá adresu této `ICorDebugValue` objektu, který se právě laděn.</span><span class="sxs-lookup"><span data-stu-id="eba1a-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="eba1a-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="eba1a-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="eba1a-113">Získá velikost v bajtech, to `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="eba1a-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="eba1a-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="eba1a-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="eba1a-115">Získá základní typ tohoto objektu `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="eba1a-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba1a-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eba1a-116">Remarks</span></span>  
 <span data-ttu-id="eba1a-117">Obecně platí vlastnictví objektu hodnotou je předána, když bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="eba1a-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="eba1a-118">Pro odebrání odkazu z objektu po dokončení se pomocí objektu zodpovídá příjemce.</span><span class="sxs-lookup"><span data-stu-id="eba1a-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="eba1a-119">V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po obnovení procesu.</span><span class="sxs-lookup"><span data-stu-id="eba1a-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="eba1a-120">Ano, obecně platí, hodnota by se neměly ukládat ve volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="eba1a-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba1a-121">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="eba1a-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba1a-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eba1a-122">Requirements</span></span>  
 <span data-ttu-id="eba1a-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eba1a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba1a-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eba1a-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eba1a-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eba1a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba1a-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba1a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba1a-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eba1a-127">See also</span></span>




- [<span data-ttu-id="eba1a-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eba1a-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="eba1a-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="eba1a-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
