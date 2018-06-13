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
ms.openlocfilehash: 9721d88c8ce138b19c98f113d9eb034c5e1c55dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417687"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="cc607-102">ICorDebugManagedCallback::CreateThread – metoda</span><span class="sxs-lookup"><span data-stu-id="cc607-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="cc607-103">Upozorní ladicí program, že vlákno byla spuštěna spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cc607-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc607-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc607-104">Syntax</span></span>  
  
```  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc607-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc607-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="cc607-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="cc607-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="cc607-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="cc607-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc607-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc607-108">Remarks</span></span>  
 <span data-ttu-id="cc607-109">Vlákno bude umístěný na první pokynů spravovaného kódu a provést.</span><span class="sxs-lookup"><span data-stu-id="cc607-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc607-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc607-110">Requirements</span></span>  
 <span data-ttu-id="cc607-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc607-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc607-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc607-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc607-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc607-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc607-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc607-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc607-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc607-115">See Also</span></span>  
 [<span data-ttu-id="cc607-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc607-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
