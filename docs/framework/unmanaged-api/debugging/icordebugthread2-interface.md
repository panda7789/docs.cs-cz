---
title: Icordebugthread2 – Interface1
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
ms.openlocfilehash: c348cf28a6330523d1a490c136a3214e37d13f4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423046"
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="5d317-102">Icordebugthread2 – Interface1</span><span class="sxs-lookup"><span data-stu-id="5d317-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="5d317-103">Slouží jako logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="5d317-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d317-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d317-104">Methods</span></span>  
  
|<span data-ttu-id="5d317-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-105">Method</span></span>|<span data-ttu-id="5d317-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5d317-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d317-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="5d317-108">Získá pole cor_active_function – instancí, které obsahují údaje o active funkcí v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="5d317-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="5d317-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="5d317-110">Získá identifikátor připojení pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="5d317-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="5d317-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="5d317-112">Získá identifikátor úlohy pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="5d317-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="5d317-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="5d317-114">Získá identifikátor operační systém pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="5d317-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="5d317-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="5d317-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="5d317-116">Umožňuje debugger zachytávat aktuální výjimky na vlákno.</span><span class="sxs-lookup"><span data-stu-id="5d317-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d317-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d317-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d317-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5d317-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d317-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d317-119">Requirements</span></span>  
 <span data-ttu-id="5d317-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d317-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d317-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d317-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d317-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d317-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d317-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d317-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d317-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d317-124">See Also</span></span>  
 [<span data-ttu-id="5d317-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5d317-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
