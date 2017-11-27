---
title: ICorDebugValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue
helpviewer_keywords: ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01c94df1d8e6ddef0110268461a2b28f594201b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="02979-102">ICorDebugValue Interface1</span><span class="sxs-lookup"><span data-stu-id="02979-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="02979-103">Reprezentuje hodnotu v procesu laděné.</span><span class="sxs-lookup"><span data-stu-id="02979-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="02979-104">Hodnota může být pro čtení nebo zápisu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02979-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02979-105">Metody</span><span class="sxs-lookup"><span data-stu-id="02979-105">Methods</span></span>  
  
|<span data-ttu-id="02979-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="02979-106">Method</span></span>|<span data-ttu-id="02979-107">Popis</span><span class="sxs-lookup"><span data-stu-id="02979-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02979-108">Createbreakpoint – metoda</span><span class="sxs-lookup"><span data-stu-id="02979-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="02979-109">Tato metoda není implementována aktuálně.</span><span class="sxs-lookup"><span data-stu-id="02979-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="02979-110">Getaddress – metoda</span><span class="sxs-lookup"><span data-stu-id="02979-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="02979-111">Získá adresu tohoto `ICorDebugValue` objekt, který je právě probíhá ladit.</span><span class="sxs-lookup"><span data-stu-id="02979-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="02979-112">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="02979-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="02979-113">Získá velikost v bajtech to `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="02979-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="02979-114">GETTYPE – metoda</span><span class="sxs-lookup"><span data-stu-id="02979-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="02979-115">Získá primitivní typ tohoto objektu `ICorDebugValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="02979-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02979-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02979-116">Remarks</span></span>  
 <span data-ttu-id="02979-117">Obecně platí vlastnictví objekt hodnoty se předá, když se vrátí.</span><span class="sxs-lookup"><span data-stu-id="02979-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="02979-118">Pro odebrání odkaz z objektu po dokončení s daným objektem zodpovídá příjemce.</span><span class="sxs-lookup"><span data-stu-id="02979-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="02979-119">V závislosti na tom, kde hodnota byla načtena z nemusí zůstat hodnotu platnou po dokončení opravy.</span><span class="sxs-lookup"><span data-stu-id="02979-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="02979-120">Ano, obecně hodnota by neměla uchovávat prostřednictvím volání z [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="02979-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02979-121">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="02979-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02979-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02979-122">Requirements</span></span>  
 <span data-ttu-id="02979-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02979-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02979-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02979-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02979-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02979-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02979-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02979-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02979-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="02979-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="02979-128">ICorDebugValue3 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="02979-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="02979-129">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="02979-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
