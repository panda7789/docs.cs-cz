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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966866"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="f9bc7-102">ICorDebugValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9bc7-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="f9bc7-103">Představuje hodnotu v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="f9bc7-104">Hodnota může být čtení nebo hodnota zápisu.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9bc7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f9bc7-105">Methods</span></span>  
  
|<span data-ttu-id="f9bc7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9bc7-106">Method</span></span>|<span data-ttu-id="f9bc7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9bc7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9bc7-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="f9bc7-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="f9bc7-109">Tato metoda není v současnosti implementována.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="f9bc7-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="f9bc7-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="f9bc7-111">Získá adresu tohoto `ICorDebugValue` objektu, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="f9bc7-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="f9bc7-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="f9bc7-113">Získá velikost tohoto `ICorDebugValue` objektu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="f9bc7-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="f9bc7-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="f9bc7-115">Získá primitivní typ tohoto `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9bc7-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9bc7-116">Remarks</span></span>  
 <span data-ttu-id="f9bc7-117">Obecně platí, že vlastnictví objektu hodnoty je předáno při jeho vrácení.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="f9bc7-118">Příjemce je zodpovědný za odebrání odkazu z objektu po jeho dokončení s objektem.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="f9bc7-119">V závislosti na tom, odkud byla hodnota načtena, nemusí tato hodnota po obnovení procesu zůstat platná.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="f9bc7-120">Obecně platí, že hodnota by neměla být držena v rámci volání metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f9bc7-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9bc7-121">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f9bc7-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9bc7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9bc7-122">Requirements</span></span>  
 <span data-ttu-id="f9bc7-123">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9bc7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9bc7-124">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9bc7-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9bc7-125">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9bc7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9bc7-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9bc7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9bc7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9bc7-127">See also</span></span>

- [<span data-ttu-id="f9bc7-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9bc7-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="f9bc7-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f9bc7-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
