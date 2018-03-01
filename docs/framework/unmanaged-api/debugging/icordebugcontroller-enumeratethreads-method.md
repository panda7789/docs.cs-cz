---
title: "ICorDebugController::EnumerateThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61d96aa6c8ae4a50c3afbcd84033244208e2444d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="da29b-102">ICorDebugController::EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="da29b-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="da29b-103">Získá enumerátor pro aktivní spravovaných vláken v procesu.</span><span class="sxs-lookup"><span data-stu-id="da29b-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da29b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da29b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da29b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da29b-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="da29b-106">[out] Ukazatel na adresu "ICorDebugThreadEnum" objekt, který reprezentuje enumerátor pro všechny spravované vláken, které jsou aktivní v procesu.</span><span class="sxs-lookup"><span data-stu-id="da29b-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da29b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da29b-107">Remarks</span></span>  
 <span data-ttu-id="da29b-108">Vlákno je považováno za aktivní po [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) zpětného volání byla odeslána a před [icordebugmanagedcallback::ExitThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) zpětného volání byla odeslána. .</span><span class="sxs-lookup"><span data-stu-id="da29b-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="da29b-109">Spravované vlákno nemusí mít nutně žádné spravované rámce v jeho zásobníku.</span><span class="sxs-lookup"><span data-stu-id="da29b-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="da29b-110">Vlákna mohou být i před uvedené [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="da29b-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="da29b-111">Výčet přirozeně bude prázdný.</span><span class="sxs-lookup"><span data-stu-id="da29b-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da29b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da29b-112">Requirements</span></span>  
 <span data-ttu-id="da29b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da29b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da29b-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da29b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da29b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da29b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da29b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da29b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da29b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="da29b-117">See Also</span></span>  
 
