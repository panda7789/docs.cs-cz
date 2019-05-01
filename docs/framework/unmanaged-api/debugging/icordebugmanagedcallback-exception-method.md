---
title: ICorDebugManagedCallback::Exception – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91318ea596cc7d6c8a747901fea2749a64aa2623
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995407"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="d43cc-102">ICorDebugManagedCallback::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="d43cc-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="d43cc-103">Upozorní ladicího programu, že byla vyvolána výjimka ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="d43cc-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d43cc-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d43cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d43cc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d43cc-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="d43cc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d43cc-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, ve kterém byla výjimka vydána.</span><span class="sxs-lookup"><span data-stu-id="d43cc-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="d43cc-108">[in] Pokud je tato hodnota `false`, výjimky nebyl dosud byl zpracovaná aplikace; v opačném případě, výjimka neošetřená a bude ukončen proces.</span><span class="sxs-lookup"><span data-stu-id="d43cc-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d43cc-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d43cc-109">Remarks</span></span>  
 <span data-ttu-id="d43cc-110">Specifické výjimky mohou být načteny z objektu vlákna.</span><span class="sxs-lookup"><span data-stu-id="d43cc-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43cc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d43cc-111">Requirements</span></span>  
 <span data-ttu-id="d43cc-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d43cc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43cc-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d43cc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d43cc-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d43cc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d43cc-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43cc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43cc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d43cc-116">See also</span></span>

- [<span data-ttu-id="d43cc-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d43cc-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
