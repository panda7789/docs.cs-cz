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
ms.openlocfilehash: c142b9656af2031b10de239645da76835c435655
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789227"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="0bb03-102">CorDebugUserState – výčet</span><span class="sxs-lookup"><span data-stu-id="0bb03-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="0bb03-103">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="0bb03-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bb03-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="0bb03-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0bb03-105">Members</span></span>  
  
|<span data-ttu-id="0bb03-106">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0bb03-106">Value</span></span>|<span data-ttu-id="0bb03-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0bb03-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="0bb03-108">Bylo vyžádáno ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="0bb03-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="0bb03-109">Bylo vyžádáno pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="0bb03-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="0bb03-110">Vlákno je spuštěno na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0bb03-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="0bb03-111">Vlákno nezahájilo provádění.</span><span class="sxs-lookup"><span data-stu-id="0bb03-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="0bb03-112">Vlákno bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="0bb03-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="0bb03-113">Vlákno čeká na dokončení úlohy jiným vláknem.</span><span class="sxs-lookup"><span data-stu-id="0bb03-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="0bb03-114">Vlákno bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="0bb03-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="0bb03-115">Vlákno je v nebezpečném bodě.</span><span class="sxs-lookup"><span data-stu-id="0bb03-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="0bb03-116">To znamená, že vlákno je v okamžiku spuštění, kde může blokovat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0bb03-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="0bb03-117">Události ladění mohou být odesílány z nebezpečných bodů, ale pozastavení vlákna v nezabezpečeném bodě pravděpodobně způsobí zablokování až do obnovení vlákna.</span><span class="sxs-lookup"><span data-stu-id="0bb03-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="0bb03-118">Bezpečné a nebezpečné body jsou určeny implementací JIT (just-in-time) a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="0bb03-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="0bb03-119">Vlákno je z fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="0bb03-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bb03-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bb03-120">Remarks</span></span>  
 <span data-ttu-id="0bb03-121">Stav uživatele vlákna je stav, který vlákno má, když ho prohlíží ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0bb03-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="0bb03-122">Vlákno může obsahovat kombinaci stavů uživatele.</span><span class="sxs-lookup"><span data-stu-id="0bb03-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="0bb03-123">Pro načtení stavu uživatele vlákna použijte metodu [ICorDebugThread:: GetUserState –](icordebugthread-getuserstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0bb03-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bb03-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bb03-124">Requirements</span></span>  
 <span data-ttu-id="0bb03-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bb03-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb03-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bb03-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bb03-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bb03-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bb03-128">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb03-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb03-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0bb03-129">See also</span></span>

- [<span data-ttu-id="0bb03-130">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0bb03-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
