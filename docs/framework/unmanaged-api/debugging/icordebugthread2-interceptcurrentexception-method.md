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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b883a5c6dd0cff119ff09747d32c607ac7ec60
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500990"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="729d1-102">ICorDebugThread2::InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="729d1-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="729d1-103">Umožňuje ladicího programu a zachytit aktuální výjimku v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="729d1-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="729d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="729d1-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="729d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="729d1-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="729d1-106">[in] Ukazatel na ICorDebugFrame, představující aktivní blok zásobníku.</span><span class="sxs-lookup"><span data-stu-id="729d1-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="729d1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="729d1-107">Remarks</span></span>  
 <span data-ttu-id="729d1-108">`InterceptCurrentException` Metodu lze volat mezi zpětného volání k výjimce ([icordebugmanagedcallback::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) nebo [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) a přidružené volání [Icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="729d1-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="729d1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="729d1-109">Requirements</span></span>  
 <span data-ttu-id="729d1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="729d1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="729d1-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="729d1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="729d1-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="729d1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="729d1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="729d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
