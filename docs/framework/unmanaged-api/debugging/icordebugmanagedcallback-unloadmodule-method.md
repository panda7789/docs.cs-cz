---
title: ICorDebugManagedCallback::UnloadModule – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f2b65b65a5e15239f731ddcb471ee7548e1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638054"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="7634f-102">ICorDebugManagedCallback::UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7634f-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="7634f-103">Upozorní ladicího programu, že společný modul runtime jazyka (DLL) byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="7634f-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7634f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7634f-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7634f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7634f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7634f-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahoval modulu.</span><span class="sxs-lookup"><span data-stu-id="7634f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="7634f-107">[in] Ukazatel na objekt icordebugmodule –, který představuje modul.</span><span class="sxs-lookup"><span data-stu-id="7634f-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7634f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7634f-108">Remarks</span></span>  
 <span data-ttu-id="7634f-109">V modulu nesmí používat po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="7634f-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7634f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7634f-110">Requirements</span></span>  
 <span data-ttu-id="7634f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7634f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7634f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7634f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7634f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7634f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7634f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7634f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7634f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7634f-115">See also</span></span>
- [<span data-ttu-id="7634f-116">LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7634f-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="7634f-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7634f-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
