---
title: "CorDebugUserState – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUserState
helpviewer_keywords: CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 95240dfea92a4ebbf2c7b9c11b7376d912c40fe5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="6e72a-102">CorDebugUserState – výčet</span><span class="sxs-lookup"><span data-stu-id="6e72a-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="6e72a-103">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="6e72a-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e72a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e72a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="6e72a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6e72a-105">Members</span></span>  
  
|<span data-ttu-id="6e72a-106">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6e72a-106">Value</span></span>|<span data-ttu-id="6e72a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6e72a-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="6e72a-108">Byla vyžádána ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="6e72a-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="6e72a-109">Byla vyžádána pozastavení vlákno.</span><span class="sxs-lookup"><span data-stu-id="6e72a-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="6e72a-110">Vlákno je spuštěno na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6e72a-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="6e72a-111">Vlákno nebyla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="6e72a-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="6e72a-112">Vlákno byla ukončena.</span><span class="sxs-lookup"><span data-stu-id="6e72a-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="6e72a-113">Vlákno čeká další vlákno k dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="6e72a-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="6e72a-114">Vlákno bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="6e72a-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="6e72a-115">Vlákno je na bod unsafe.</span><span class="sxs-lookup"><span data-stu-id="6e72a-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="6e72a-116">To znamená vlákno je na místo v provádění kde může toto blokování uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e72a-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="6e72a-117">Ladění událostí může odeslat z bodů unsafe, ale pozastavení vlákna na bod unsafe velmi pravděpodobně zablokování způsobí dokud vlákno obnovení.</span><span class="sxs-lookup"><span data-stu-id="6e72a-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="6e72a-118">Bezpečné a unsafe body jsou určeny v běhu (JIT) a implementaci kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="6e72a-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="6e72a-119">Vlákno je z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="6e72a-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e72a-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e72a-120">Remarks</span></span>  
 <span data-ttu-id="6e72a-121">Stav uživatele vlákno je stav, který má vlákno při prozkoumá ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="6e72a-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="6e72a-122">Vlákno může mít kombinaci stavů uživatele.</span><span class="sxs-lookup"><span data-stu-id="6e72a-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="6e72a-123">Použití [icordebugthread::getuserstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metoda pro načtení stavu uživatele vlákno.</span><span class="sxs-lookup"><span data-stu-id="6e72a-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e72a-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e72a-124">Requirements</span></span>  
 <span data-ttu-id="6e72a-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e72a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e72a-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e72a-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e72a-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e72a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e72a-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e72a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e72a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e72a-129">See Also</span></span>  
 [<span data-ttu-id="6e72a-130">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="6e72a-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
