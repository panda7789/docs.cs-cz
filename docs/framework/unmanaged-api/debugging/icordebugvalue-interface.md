---
title: ICorDebugValue Interface1
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
ms.openlocfilehash: 0fe53490014a2a7d9acc0a426613af54867599e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422120"
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="b9f02-102">ICorDebugValue Interface1</span><span class="sxs-lookup"><span data-stu-id="b9f02-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="b9f02-103">Reprezentuje hodnotu v procesu laděné.</span><span class="sxs-lookup"><span data-stu-id="b9f02-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="b9f02-104">Hodnota může být pro čtení nebo zápisu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b9f02-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9f02-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b9f02-105">Methods</span></span>  
  
|<span data-ttu-id="b9f02-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9f02-106">Method</span></span>|<span data-ttu-id="b9f02-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b9f02-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9f02-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="b9f02-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="b9f02-109">Tato metoda není implementována aktuálně.</span><span class="sxs-lookup"><span data-stu-id="b9f02-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="b9f02-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="b9f02-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="b9f02-111">Získá adresu tohoto `ICorDebugValue` objekt, který je právě probíhá ladit.</span><span class="sxs-lookup"><span data-stu-id="b9f02-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="b9f02-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b9f02-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="b9f02-113">Získá velikost v bajtech to `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="b9f02-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="b9f02-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="b9f02-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="b9f02-115">Získá primitivní typ tohoto objektu `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="b9f02-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f02-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9f02-116">Remarks</span></span>  
 <span data-ttu-id="b9f02-117">Obecně platí vlastnictví objekt hodnoty se předá, když se vrátí.</span><span class="sxs-lookup"><span data-stu-id="b9f02-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="b9f02-118">Pro odebrání odkaz z objektu po dokončení s daným objektem zodpovídá příjemce.</span><span class="sxs-lookup"><span data-stu-id="b9f02-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="b9f02-119">V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po dokončení opravy.</span><span class="sxs-lookup"><span data-stu-id="b9f02-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="b9f02-120">Ano, obecně hodnota by neměla uchovávat prostřednictvím volání z [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="b9f02-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9f02-121">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b9f02-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9f02-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9f02-122">Requirements</span></span>  
 <span data-ttu-id="b9f02-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9f02-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9f02-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9f02-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9f02-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9f02-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9f02-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9f02-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f02-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9f02-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="b9f02-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9f02-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="b9f02-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b9f02-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
