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
ms.openlocfilehash: 2ca11853100228287c4148a2330cbc5a4609550f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472505"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="2fdd6-102">ICorDebugManagedCallback::CreateThread – metoda</span><span class="sxs-lookup"><span data-stu-id="2fdd6-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="2fdd6-103">Upozorní ladicí program, vlákno se zahájilo se spuštění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2fdd6-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fdd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fdd6-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fdd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fdd6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2fdd6-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, která obsahuje vlákna.</span><span class="sxs-lookup"><span data-stu-id="2fdd6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="2fdd6-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="2fdd6-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fdd6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fdd6-108">Remarks</span></span>  
 <span data-ttu-id="2fdd6-109">Vlákno bude nastavený na první instrukce pro spravovaný kód má být proveden.</span><span class="sxs-lookup"><span data-stu-id="2fdd6-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fdd6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fdd6-110">Requirements</span></span>  
 <span data-ttu-id="2fdd6-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fdd6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fdd6-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fdd6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fdd6-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fdd6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fdd6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fdd6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fdd6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fdd6-115">See also</span></span>
- [<span data-ttu-id="2fdd6-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2fdd6-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
