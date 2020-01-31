---
title: ICorDebugController::EnumerateThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783787"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="bf448-102">ICorDebugController::EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="bf448-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="bf448-103">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="bf448-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf448-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf448-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf448-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf448-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="bf448-106">mimo Ukazatel na adresu objektu "ICorDebugThreadEnum", který představuje enumerátor pro všechna spravovaná vlákna, která jsou v procesu aktivní.</span><span class="sxs-lookup"><span data-stu-id="bf448-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf448-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf448-107">Remarks</span></span>  
 <span data-ttu-id="bf448-108">Vlákno je považováno za aktivní po odeslání zpětného volání [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) a před odesláním zpětného volání [ICorDebugManagedCallback:: ExitThread –](icordebugmanagedcallback-exitthread-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf448-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="bf448-109">Spravované vlákno nemusí mít nutně žádné spravované snímky v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf448-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="bf448-110">Vlákna lze vyčíslit i před zpětným voláním [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf448-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="bf448-111">Výčet bude přirozeně prázdný.</span><span class="sxs-lookup"><span data-stu-id="bf448-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf448-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf448-112">Requirements</span></span>  
 <span data-ttu-id="bf448-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf448-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf448-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bf448-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf448-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bf448-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf448-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf448-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf448-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf448-117">See also</span></span>
