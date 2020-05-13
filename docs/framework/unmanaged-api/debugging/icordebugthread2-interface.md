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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379836"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="f0118-102">ICorDebugThread2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0118-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="f0118-103">Slouží jako logické rozšíření rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f0118-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0118-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0118-104">Methods</span></span>  
  
|<span data-ttu-id="f0118-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-105">Method</span></span>|<span data-ttu-id="f0118-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f0118-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0118-107">GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="f0118-108">Získá pole instancí COR_ACTIVE_FUNCTION, které obsahují data o aktivních funkcích v rámečcích vlákna.</span><span class="sxs-lookup"><span data-stu-id="f0118-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="f0118-109">GetConnectionID – metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="f0118-110">Získá identifikátor připojení `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="f0118-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f0118-111">GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="f0118-112">Načte identifikátor úkolu `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="f0118-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f0118-113">GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="f0118-114">Získá identifikátor vlákna operačního systému `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="f0118-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="f0118-115">InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="f0118-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="f0118-116">Umožňuje ladicímu programu zachytit aktuální výjimku ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="f0118-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0118-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0118-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0118-118">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f0118-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0118-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f0118-119">Requirements</span></span>  
 <span data-ttu-id="f0118-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0118-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0118-121">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0118-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0118-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f0118-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0118-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0118-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0118-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0118-124">See also</span></span>

- [<span data-ttu-id="f0118-125">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f0118-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
