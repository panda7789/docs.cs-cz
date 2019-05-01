---
title: ICorDebugThread2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993938"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="ce3b9-102">ICorDebugThread2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce3b9-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="ce3b9-103">Slouží jako logické rozšíření pro icordebugthread – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ce3b9-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ce3b9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ce3b9-104">Methods</span></span>  
  
|<span data-ttu-id="ce3b9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-105">Method</span></span>|<span data-ttu-id="ce3b9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ce3b9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ce3b9-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="ce3b9-108">Získává pole cor_active_function – instance, které obsahují údaje o aktivní funkce v rámcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="ce3b9-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="ce3b9-110">Získá identifikátor připojení pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="ce3b9-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="ce3b9-112">Získá identifikátor úlohy pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="ce3b9-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="ce3b9-114">Získá identifikátor vlákna operačního systému pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="ce3b9-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b9-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="ce3b9-116">Umožňuje ladicího programu a zachytit aktuální výjimku ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce3b9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce3b9-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce3b9-118">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="ce3b9-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce3b9-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce3b9-119">Requirements</span></span>  
 <span data-ttu-id="ce3b9-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce3b9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce3b9-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce3b9-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce3b9-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce3b9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce3b9-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3b9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3b9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce3b9-124">See also</span></span>

- [<span data-ttu-id="ce3b9-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ce3b9-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
