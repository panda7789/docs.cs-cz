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
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138670"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="9eacc-102">ICorDebugThread2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9eacc-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="9eacc-103">Slouží jako logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9eacc-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9eacc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9eacc-104">Methods</span></span>  
  
|<span data-ttu-id="9eacc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-105">Method</span></span>|<span data-ttu-id="9eacc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9eacc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9eacc-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="9eacc-108">Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="9eacc-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="9eacc-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="9eacc-110">Získá identifikátor připojení pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="9eacc-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="9eacc-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="9eacc-112">Získá identifikátor úkolu pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="9eacc-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="9eacc-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="9eacc-114">Získá identifikátor vlákna operačního systému pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="9eacc-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="9eacc-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="9eacc-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="9eacc-116">Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="9eacc-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eacc-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9eacc-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9eacc-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9eacc-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eacc-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9eacc-119">Requirements</span></span>  
 <span data-ttu-id="9eacc-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eacc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eacc-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9eacc-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eacc-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9eacc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eacc-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eacc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eacc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9eacc-124">See also</span></span>

- [<span data-ttu-id="9eacc-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9eacc-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
