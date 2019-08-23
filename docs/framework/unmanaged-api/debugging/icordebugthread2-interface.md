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
ms.openlocfilehash: 4d21c221bba3ac668924003f96580bb660229ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963007"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="58203-102">ICorDebugThread2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58203-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="58203-103">Slouží jako logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="58203-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58203-104">Metody</span><span class="sxs-lookup"><span data-stu-id="58203-104">Methods</span></span>  
  
|<span data-ttu-id="58203-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="58203-105">Method</span></span>|<span data-ttu-id="58203-106">Popis</span><span class="sxs-lookup"><span data-stu-id="58203-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58203-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="58203-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="58203-108">Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="58203-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="58203-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="58203-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="58203-110">Získá identifikátor `ICorDebugThread2`připojení.</span><span class="sxs-lookup"><span data-stu-id="58203-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="58203-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="58203-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="58203-112">Načte identifikátor `ICorDebugThread2`úkolu.</span><span class="sxs-lookup"><span data-stu-id="58203-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="58203-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="58203-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="58203-114">Získá identifikátor `ICorDebugThread2`vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="58203-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="58203-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="58203-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="58203-116">Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="58203-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58203-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58203-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58203-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="58203-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58203-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58203-119">Requirements</span></span>  
 <span data-ttu-id="58203-120">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58203-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58203-121">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="58203-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58203-122">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58203-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58203-123">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58203-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58203-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58203-124">See also</span></span>

- [<span data-ttu-id="58203-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="58203-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
