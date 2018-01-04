---
title: "Icordebugthread2 – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 907ba524164b1e0d167f7a88250c7d32910504f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="b1191-102">Icordebugthread2 – Interface1</span><span class="sxs-lookup"><span data-stu-id="b1191-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="b1191-103">Slouží jako logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b1191-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1191-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1191-104">Methods</span></span>  
  
|<span data-ttu-id="b1191-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-105">Method</span></span>|<span data-ttu-id="b1191-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b1191-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1191-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="b1191-108">Získá pole cor_active_function – instancí, které obsahují údaje o active funkcí v podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="b1191-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="b1191-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="b1191-110">Získá identifikátor připojení pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b1191-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b1191-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="b1191-112">Získá identifikátor úlohy pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b1191-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b1191-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="b1191-114">Získá identifikátor operační systém pro tento `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b1191-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b1191-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="b1191-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="b1191-116">Umožňuje debugger zachytávat aktuální výjimky na vlákno.</span><span class="sxs-lookup"><span data-stu-id="b1191-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1191-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1191-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1191-118">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b1191-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1191-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1191-119">Requirements</span></span>  
 <span data-ttu-id="b1191-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1191-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1191-121">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1191-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1191-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1191-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1191-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1191-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1191-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1191-124">See Also</span></span>  
 [<span data-ttu-id="b1191-125">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b1191-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
