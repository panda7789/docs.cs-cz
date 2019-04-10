---
title: ICorDebugManagedCallback::CreateThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c48e92c73347957d8acc5c209f6f5473e9e18524
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223248"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="015af-102">ICorDebugManagedCallback::CreateThread – metoda</span><span class="sxs-lookup"><span data-stu-id="015af-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="015af-103">Upozorní ladicí program, vlákno se zahájilo se spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="015af-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="015af-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="015af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="015af-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="015af-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která obsahuje vlákna.</span><span class="sxs-lookup"><span data-stu-id="015af-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="015af-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="015af-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="015af-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="015af-108">Remarks</span></span>  
 <span data-ttu-id="015af-109">Vlákno bude nastavený na první instrukce pro spravovaný kód má být proveden.</span><span class="sxs-lookup"><span data-stu-id="015af-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="015af-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="015af-110">Requirements</span></span>  
 <span data-ttu-id="015af-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="015af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="015af-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="015af-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="015af-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="015af-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="015af-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="015af-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="015af-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="015af-115">See also</span></span>

- [<span data-ttu-id="015af-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="015af-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
