---
title: CorDebugUserState – výčet
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d502b4098016fb14793bccd6feb641e92e3c2611
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795635"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="b002b-102">CorDebugUserState – výčet</span><span class="sxs-lookup"><span data-stu-id="b002b-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="b002b-103">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="b002b-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b002b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b002b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b002b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b002b-105">Members</span></span>  
  
|<span data-ttu-id="b002b-106">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b002b-106">Value</span></span>|<span data-ttu-id="b002b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b002b-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="b002b-108">Bylo vyžádáno ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="b002b-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="b002b-109">Bylo vyžádáno pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="b002b-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="b002b-110">Vlákno je spuštěno na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b002b-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="b002b-111">Vlákno nezahájilo provádění.</span><span class="sxs-lookup"><span data-stu-id="b002b-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="b002b-112">Vlákno bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="b002b-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="b002b-113">Vlákno čeká na dokončení úlohy jiným vláknem.</span><span class="sxs-lookup"><span data-stu-id="b002b-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="b002b-114">Vlákno bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="b002b-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="b002b-115">Vlákno je v nebezpečném bodě.</span><span class="sxs-lookup"><span data-stu-id="b002b-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="b002b-116">To znamená, že vlákno je v okamžiku spuštění, kde může blokovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b002b-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="b002b-117">Události ladění mohou být odesílány z nebezpečných bodů, ale pozastavení vlákna v nezabezpečeném bodě pravděpodobně způsobí zablokování až do obnovení vlákna.</span><span class="sxs-lookup"><span data-stu-id="b002b-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="b002b-118">Bezpečné a nebezpečné body jsou určeny implementací JIT (just-in-time) a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b002b-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="b002b-119">Vlákno je z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b002b-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b002b-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b002b-120">Remarks</span></span>  
 <span data-ttu-id="b002b-121">Stav uživatele vlákna je stav, který vlákno má, když ho prohlíží ladicí program.</span><span class="sxs-lookup"><span data-stu-id="b002b-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="b002b-122">Vlákno může obsahovat kombinaci stavů uživatele.</span><span class="sxs-lookup"><span data-stu-id="b002b-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="b002b-123">Pro načtení stavu uživatele vlákna použijte metodu [ICorDebugThread:: GetUserState –](icordebugthread-getuserstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b002b-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b002b-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b002b-124">Requirements</span></span>  
 <span data-ttu-id="b002b-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b002b-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b002b-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b002b-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b002b-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b002b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b002b-128">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b002b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b002b-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b002b-129">See also</span></span>

- [<span data-ttu-id="b002b-130">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="b002b-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
