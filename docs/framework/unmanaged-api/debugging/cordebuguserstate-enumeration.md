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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76fbbb3f924f610b604586dca78cab344217b544
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739460"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="8fe11-102">CorDebugUserState – výčet</span><span class="sxs-lookup"><span data-stu-id="8fe11-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="8fe11-103">Určuje stav uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="8fe11-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe11-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8fe11-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8fe11-105">Members</span></span>  
  
|<span data-ttu-id="8fe11-106">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8fe11-106">Value</span></span>|<span data-ttu-id="8fe11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fe11-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="8fe11-108">Bylo vyžádáno ukončení vlákna.</span><span class="sxs-lookup"><span data-stu-id="8fe11-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="8fe11-109">Se požaduje pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="8fe11-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="8fe11-110">Vlákno je spuštěno na pozadí.</span><span class="sxs-lookup"><span data-stu-id="8fe11-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="8fe11-111">Vlákno není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="8fe11-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="8fe11-112">Vlákno bylo ukončeno.</span><span class="sxs-lookup"><span data-stu-id="8fe11-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="8fe11-113">Vlákno čeká další vlákno k dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="8fe11-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="8fe11-114">Vlákno bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="8fe11-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="8fe11-115">Vlákno je nebezpečné okamžiku.</span><span class="sxs-lookup"><span data-stu-id="8fe11-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="8fe11-116">Vlákno je v bodě provádění kde blokuje uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="8fe11-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="8fe11-117">Ladění události může být z něj odešle nebezpečné body, ale nebezpečné okamžiku pozastavení vlákna budou velmi pravděpodobné, že k vzájemnému zablokování až se obnoví vlákno.</span><span class="sxs-lookup"><span data-stu-id="8fe11-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="8fe11-118">Bezpečné a unsafe body jsou určeny just-in-time (JIT) a implementaci kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8fe11-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="8fe11-119">Vlákno je z fondu podprocesů.</span><span class="sxs-lookup"><span data-stu-id="8fe11-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fe11-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fe11-120">Remarks</span></span>  
 <span data-ttu-id="8fe11-121">Stav uživatele vlákna je stav, který má vlákna prozkoumá ladicí program.</span><span class="sxs-lookup"><span data-stu-id="8fe11-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="8fe11-122">Vlákno může mít kombinaci stavů uživatele.</span><span class="sxs-lookup"><span data-stu-id="8fe11-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="8fe11-123">Použití [icordebugthread::getuserstate –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metody k získání stavu uživatele vlákna.</span><span class="sxs-lookup"><span data-stu-id="8fe11-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe11-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fe11-124">Requirements</span></span>  
 <span data-ttu-id="8fe11-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe11-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe11-126">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fe11-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fe11-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe11-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe11-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe11-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe11-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe11-129">See also</span></span>

- [<span data-ttu-id="8fe11-130">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="8fe11-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
