---
title: ICorDebugManagedCallback::NameChange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a7ef478fed697f4152a6348931ddf3b4b4b2885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415006"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="80aa1-102">ICorDebugManagedCallback::NameChange – metoda</span><span class="sxs-lookup"><span data-stu-id="80aa1-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="80aa1-103">Upozorní ladicí program, že došlo ke změně názvu domény aplikace nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="80aa1-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80aa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80aa1-104">Syntax</span></span>  
  
```  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80aa1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80aa1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="80aa1-106">[v] Ukazatel na ICorDebugAppDomain objekt, který reprezentuje doméně aplikace, která buď měl změnu názvu nebo který obsahuje vláken, která měla změnit název.</span><span class="sxs-lookup"><span data-stu-id="80aa1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="80aa1-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, která měla změnit název.</span><span class="sxs-lookup"><span data-stu-id="80aa1-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80aa1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="80aa1-108">Requirements</span></span>  
 <span data-ttu-id="80aa1-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80aa1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80aa1-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80aa1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80aa1-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80aa1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80aa1-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80aa1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80aa1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="80aa1-113">See Also</span></span>  
 [<span data-ttu-id="80aa1-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="80aa1-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
