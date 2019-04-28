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
ms.openlocfilehash: 17ba15553d2e7dcd2090870eaab54b4c680631f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749342"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="70860-102">ICorDebugController::EnumerateThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="70860-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="70860-103">Získá enumerátor pro aktivní spravovaná vlákna v procesu.</span><span class="sxs-lookup"><span data-stu-id="70860-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70860-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70860-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70860-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70860-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="70860-106">[out] Ukazatel na adresu objektu "icordebugthreadenum –", který představuje enumerátor pro všechna spravovaná vlákna, které jsou aktivní v procesu.</span><span class="sxs-lookup"><span data-stu-id="70860-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70860-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70860-107">Remarks</span></span>  
 <span data-ttu-id="70860-108">Vlákno se považuje za aktivní po [icordebugmanagedcallback::CreateThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) byly odeslány zpětného volání a před [icordebugmanagedcallback::ExitThread –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) zpětného volání byly odeslány. .</span><span class="sxs-lookup"><span data-stu-id="70860-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="70860-109">Spravované vlákno nemusí mít nutně žádné spravované bloky na svůj zásobník.</span><span class="sxs-lookup"><span data-stu-id="70860-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="70860-110">Vlákna mohou být ještě před uvedené [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="70860-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="70860-111">Výčet přirozeně bude prázdný.</span><span class="sxs-lookup"><span data-stu-id="70860-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70860-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70860-112">Requirements</span></span>  
 <span data-ttu-id="70860-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70860-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70860-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70860-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70860-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70860-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70860-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70860-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70860-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70860-117">See also</span></span>
