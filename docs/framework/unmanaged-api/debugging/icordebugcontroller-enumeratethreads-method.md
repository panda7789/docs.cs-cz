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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a4bb4072c574edeac1c531978fac75595c252e0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481596"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="b8cb5-102">ICorDebugController::EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b8cb5-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="b8cb5-103">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="b8cb5-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8cb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8cb5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8cb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8cb5-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="b8cb5-106">[out] Ukazatel na adresu objektu "icordebugthreadenum –", který představuje enumerátor pro všechna spravovaná vlákna, které jsou aktivní v procesu.</span><span class="sxs-lookup"><span data-stu-id="b8cb5-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8cb5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8cb5-107">Remarks</span></span>  
 <span data-ttu-id="b8cb5-108">Vlákno se považuje za aktivní po [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) byly odeslány zpětného volání a před [icordebugmanagedcallback::ExitThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) zpětného volání byly odeslány. .</span><span class="sxs-lookup"><span data-stu-id="b8cb5-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="b8cb5-109">Spravované vlákno nemusí mít nutně žádné spravované bloky na svůj zásobník.</span><span class="sxs-lookup"><span data-stu-id="b8cb5-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="b8cb5-110">Vlákna mohou být ještě před uvedené [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b8cb5-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="b8cb5-111">Výčet přirozeně bude prázdný.</span><span class="sxs-lookup"><span data-stu-id="b8cb5-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8cb5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8cb5-112">Requirements</span></span>  
 <span data-ttu-id="b8cb5-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8cb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8cb5-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8cb5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8cb5-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8cb5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8cb5-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8cb5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cb5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8cb5-117">See also</span></span>

