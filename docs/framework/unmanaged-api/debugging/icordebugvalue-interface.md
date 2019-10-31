---
title: ICorDebugValue – rozhraní
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
ms.openlocfilehash: 77d28d8eef97a934c15ac29725f856f4bf39e6ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140155"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="495e0-102">ICorDebugValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="495e0-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="495e0-103">Představuje hodnotu v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="495e0-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="495e0-104">Hodnota může být čtení nebo hodnota zápisu.</span><span class="sxs-lookup"><span data-stu-id="495e0-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="495e0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="495e0-105">Methods</span></span>  
  
|<span data-ttu-id="495e0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="495e0-106">Method</span></span>|<span data-ttu-id="495e0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="495e0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="495e0-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="495e0-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="495e0-109">Tato metoda není v současnosti implementována.</span><span class="sxs-lookup"><span data-stu-id="495e0-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="495e0-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="495e0-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="495e0-111">Získá adresu tohoto objektu `ICorDebugValue`, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="495e0-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="495e0-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="495e0-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="495e0-113">Získá velikost objektu `ICorDebugValue` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="495e0-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="495e0-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="495e0-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="495e0-115">Získá primitivní typ tohoto objektu `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="495e0-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="495e0-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="495e0-116">Remarks</span></span>  
 <span data-ttu-id="495e0-117">Obecně platí, že vlastnictví objektu hodnoty je předáno při jeho vrácení.</span><span class="sxs-lookup"><span data-stu-id="495e0-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="495e0-118">Příjemce je zodpovědný za odebrání odkazu z objektu po jeho dokončení s objektem.</span><span class="sxs-lookup"><span data-stu-id="495e0-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="495e0-119">V závislosti na tom, odkud byla hodnota načtena, nemusí tato hodnota po obnovení procesu zůstat platná.</span><span class="sxs-lookup"><span data-stu-id="495e0-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="495e0-120">Obecně platí, že hodnota by neměla být držena v rámci volání metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="495e0-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="495e0-121">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="495e0-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495e0-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="495e0-122">Requirements</span></span>  
 <span data-ttu-id="495e0-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="495e0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="495e0-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="495e0-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="495e0-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="495e0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="495e0-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="495e0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495e0-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="495e0-127">See also</span></span>

- [<span data-ttu-id="495e0-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="495e0-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="495e0-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="495e0-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
