---
title: "ICorDebugThread2::InterceptCurrentException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.InterceptCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 169ce528a2a6fd6ac415989437e721509d9fcda1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="4e7ad-102">ICorDebugThread2::InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="4e7ad-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="4e7ad-103">Umožňuje debugger zachytávat aktuální výjimky na tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="4e7ad-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e7ad-104">Syntax</span></span>  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e7ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e7ad-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="4e7ad-106">[v] Ukazatel ICorDebugFrame představující active zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4e7ad-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e7ad-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e7ad-107">Remarks</span></span>  
 <span data-ttu-id="4e7ad-108">`InterceptCurrentException` Nelze volat metodu mezi zpětného volání k výjimce ([icordebugmanagedcallback::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) nebo [icordebugmanagedcallback2::Exception –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) a přidružené volání [Icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="4e7ad-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7ad-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e7ad-109">Requirements</span></span>  
 <span data-ttu-id="4e7ad-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7ad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7ad-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e7ad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e7ad-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e7ad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e7ad-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
