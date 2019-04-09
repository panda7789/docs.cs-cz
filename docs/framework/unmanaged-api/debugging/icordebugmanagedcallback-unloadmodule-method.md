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
ms.openlocfilehash: 12e42da015864e83663d2f4d74bab2a34052d760
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083541"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="bf227-102">ICorDebugManagedCallback::UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="bf227-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="bf227-103">Upozorní ladicího programu, že společný modul runtime jazyka (DLL) byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="bf227-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf227-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf227-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf227-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf227-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="bf227-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který obsahoval modulu.</span><span class="sxs-lookup"><span data-stu-id="bf227-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="bf227-107">[in] Ukazatel na objekt icordebugmodule –, který představuje modul.</span><span class="sxs-lookup"><span data-stu-id="bf227-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf227-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf227-108">Remarks</span></span>  
 <span data-ttu-id="bf227-109">V modulu nesmí používat po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="bf227-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf227-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf227-110">Requirements</span></span>  
 <span data-ttu-id="bf227-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf227-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf227-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf227-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf227-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf227-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bf227-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bf227-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf227-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf227-115">See also</span></span>

- [<span data-ttu-id="bf227-116">LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="bf227-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="bf227-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf227-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
