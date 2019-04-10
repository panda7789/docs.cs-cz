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
ms.openlocfilehash: bdc889dd6b2854654bfe43b24afbe4cc19863c80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227818"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="42656-102">ICorDebugValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42656-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="42656-103">Reprezentuje hodnotu v laděném procesu.</span><span class="sxs-lookup"><span data-stu-id="42656-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="42656-104">Hodnota může být čtení nebo zápis hodnoty.</span><span class="sxs-lookup"><span data-stu-id="42656-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42656-105">Metody</span><span class="sxs-lookup"><span data-stu-id="42656-105">Methods</span></span>  
  
|<span data-ttu-id="42656-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="42656-106">Method</span></span>|<span data-ttu-id="42656-107">Popis</span><span class="sxs-lookup"><span data-stu-id="42656-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42656-108">CreateBreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="42656-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="42656-109">Tato metoda teď není implementovaná.</span><span class="sxs-lookup"><span data-stu-id="42656-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="42656-110">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="42656-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="42656-111">Získá adresu této `ICorDebugValue` objektu, který se právě laděn.</span><span class="sxs-lookup"><span data-stu-id="42656-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="42656-112">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="42656-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="42656-113">Získá velikost v bajtech, to `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="42656-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="42656-114">GetType – metoda</span><span class="sxs-lookup"><span data-stu-id="42656-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="42656-115">Získá základní typ tohoto objektu `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="42656-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42656-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42656-116">Remarks</span></span>  
 <span data-ttu-id="42656-117">Obecně platí vlastnictví objektu hodnotou je předána, když bude vrácen.</span><span class="sxs-lookup"><span data-stu-id="42656-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="42656-118">Pro odebrání odkazu z objektu po dokončení se pomocí objektu zodpovídá příjemce.</span><span class="sxs-lookup"><span data-stu-id="42656-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="42656-119">V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po obnovení procesu.</span><span class="sxs-lookup"><span data-stu-id="42656-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="42656-120">Ano, obecně platí, hodnota by se neměly ukládat ve volání [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="42656-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42656-121">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="42656-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42656-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42656-122">Requirements</span></span>  
 <span data-ttu-id="42656-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42656-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42656-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42656-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42656-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42656-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="42656-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="42656-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="42656-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42656-127">See also</span></span>

- [<span data-ttu-id="42656-128">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42656-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="42656-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42656-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
