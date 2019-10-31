---
title: ICorDebugThread2::InterceptCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: 1f3cf3db5df610e57a957147f0ab79121679e00b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138703"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="b3793-102">ICorDebugThread2::InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="b3793-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="b3793-103">Umožňuje ladicímu programu zachytit aktuální výjimku v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="b3793-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3793-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3793-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3793-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3793-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="b3793-106">pro Ukazatel na ICorDebugFrame, který představuje aktivní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b3793-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3793-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3793-107">Remarks</span></span>  
 <span data-ttu-id="b3793-108">Metodu `InterceptCurrentException` lze volat mezi zpětným voláním výjimky ([ICorDebugManagedCallback:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) nebo [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) a přidruženým voláním [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3793-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3793-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3793-109">Requirements</span></span>  
 <span data-ttu-id="b3793-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3793-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3793-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3793-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3793-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b3793-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3793-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3793-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
