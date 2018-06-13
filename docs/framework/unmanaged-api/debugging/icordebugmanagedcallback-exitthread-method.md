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
ms.openlocfilehash: 24b01fecc7947d14e36b4411a58d200667b0f2a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415539"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="efc07-102">ICorDebugManagedCallback::ExitThread – metoda</span><span class="sxs-lookup"><span data-stu-id="efc07-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="efc07-103">Upozorní ladicí program, aby byl ukončen vláken, která byla spuštěna spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="efc07-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efc07-104">Syntax</span></span>  
  
```  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efc07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc07-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="efc07-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující spravovaných vláken.</span><span class="sxs-lookup"><span data-stu-id="efc07-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="efc07-107">[v] Ukazatel ICorDebugThread objektu, která představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="efc07-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efc07-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efc07-108">Remarks</span></span>  
 <span data-ttu-id="efc07-109">Jednou `ExitThread` zpětné volání je aktivována, vlákno se nebude zobrazovat v výčty přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="efc07-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc07-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efc07-110">Requirements</span></span>  
 <span data-ttu-id="efc07-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efc07-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc07-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efc07-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efc07-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efc07-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc07-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc07-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc07-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="efc07-115">See Also</span></span>  
 [<span data-ttu-id="efc07-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="efc07-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
