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
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791141"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="6be7b-102">ICorDebugValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be7b-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="6be7b-103">Představuje hodnotu v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="6be7b-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="6be7b-104">Hodnota může být čtení nebo hodnota zápisu.</span><span class="sxs-lookup"><span data-stu-id="6be7b-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6be7b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6be7b-105">Methods</span></span>  
  
|<span data-ttu-id="6be7b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6be7b-106">Method</span></span>|<span data-ttu-id="6be7b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6be7b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6be7b-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="6be7b-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="6be7b-109">Tato metoda není v současnosti implementována.</span><span class="sxs-lookup"><span data-stu-id="6be7b-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="6be7b-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="6be7b-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="6be7b-111">Získá adresu tohoto objektu `ICorDebugValue`, který je právě laděn.</span><span class="sxs-lookup"><span data-stu-id="6be7b-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="6be7b-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6be7b-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="6be7b-113">Získá velikost objektu `ICorDebugValue` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6be7b-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="6be7b-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="6be7b-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="6be7b-115">Získá primitivní typ tohoto objektu `ICorDebugValue`.</span><span class="sxs-lookup"><span data-stu-id="6be7b-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6be7b-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6be7b-116">Remarks</span></span>  
 <span data-ttu-id="6be7b-117">Obecně platí, že vlastnictví objektu hodnoty je předáno při jeho vrácení.</span><span class="sxs-lookup"><span data-stu-id="6be7b-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="6be7b-118">Příjemce je zodpovědný za odebrání odkazu z objektu po jeho dokončení s objektem.</span><span class="sxs-lookup"><span data-stu-id="6be7b-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="6be7b-119">V závislosti na tom, odkud byla hodnota načtena, nemusí tato hodnota po obnovení procesu zůstat platná.</span><span class="sxs-lookup"><span data-stu-id="6be7b-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="6be7b-120">Obecně platí, že hodnota by neměla být držena v rámci volání metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6be7b-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6be7b-121">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6be7b-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6be7b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6be7b-122">Requirements</span></span>  
 <span data-ttu-id="6be7b-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6be7b-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be7b-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6be7b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6be7b-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6be7b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6be7b-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be7b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be7b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6be7b-127">See also</span></span>

- [<span data-ttu-id="6be7b-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6be7b-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="6be7b-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6be7b-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
