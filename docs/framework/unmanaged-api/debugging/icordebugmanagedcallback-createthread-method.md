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
ms.openlocfilehash: 2192b5d3b240211c8982eab7539896ea3626a072
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759679"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="9ce6e-102">ICorDebugManagedCallback::CreateThread – metoda</span><span class="sxs-lookup"><span data-stu-id="9ce6e-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="9ce6e-103">Upozorní ladicí program, vlákno se zahájilo se spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9ce6e-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ce6e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ce6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ce6e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9ce6e-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která obsahuje vlákna.</span><span class="sxs-lookup"><span data-stu-id="9ce6e-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="9ce6e-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="9ce6e-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ce6e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ce6e-108">Remarks</span></span>  
 <span data-ttu-id="9ce6e-109">Vlákno bude nastavený na první instrukce pro spravovaný kód má být proveden.</span><span class="sxs-lookup"><span data-stu-id="9ce6e-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ce6e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ce6e-110">Requirements</span></span>  
 <span data-ttu-id="9ce6e-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ce6e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ce6e-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ce6e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ce6e-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ce6e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ce6e-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ce6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce6e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ce6e-115">See also</span></span>

- [<span data-ttu-id="9ce6e-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ce6e-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
