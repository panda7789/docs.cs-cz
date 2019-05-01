---
title: ICorDebugManagedCallback::ExitThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37815d8aead1ec89826c13db6f012f2cd17bc792
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988179"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="47862-102">ICorDebugManagedCallback::ExitThread – metoda</span><span class="sxs-lookup"><span data-stu-id="47862-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="47862-103">Upozorní ladicího programu, že vlákno, které se spouští spravovaný kód byl ukončen.</span><span class="sxs-lookup"><span data-stu-id="47862-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47862-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47862-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47862-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47862-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="47862-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="47862-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="47862-107">[in] Ukazatel na objekt ICorDebugThread, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="47862-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47862-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47862-108">Remarks</span></span>  
 <span data-ttu-id="47862-109">Jakmile `ExitThread` zpětné volání se aktivuje, vlákno se nebude zobrazovat ve vlákno výčtech.</span><span class="sxs-lookup"><span data-stu-id="47862-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47862-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47862-110">Requirements</span></span>  
 <span data-ttu-id="47862-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47862-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47862-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47862-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47862-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47862-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47862-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47862-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47862-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47862-115">See also</span></span>

- [<span data-ttu-id="47862-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47862-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
