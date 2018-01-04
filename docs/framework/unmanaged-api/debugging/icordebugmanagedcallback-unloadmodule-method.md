---
title: "ICorDebugManagedCallback::UnloadModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.UnloadModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7aeb3f12d5217c57d8d8f1f5665840a4515c0998
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="7c2b5-102">ICorDebugManagedCallback::UnloadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7c2b5-102">ICorDebugManagedCallback::UnloadModule Method</span></span>
<span data-ttu-id="7c2b5-103">Upozorní ladicího programu běžné modulu runtime jazyka (DLL) byl odpojen.</span><span class="sxs-lookup"><span data-stu-id="7c2b5-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c2b5-104">Syntax</span></span>  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c2b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c2b5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="7c2b5-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, která obsahovala modul.</span><span class="sxs-lookup"><span data-stu-id="7c2b5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="7c2b5-107">[v] Ukazatel na ICorDebugModule objekt, který představuje modul.</span><span class="sxs-lookup"><span data-stu-id="7c2b5-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c2b5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c2b5-108">Remarks</span></span>  
 <span data-ttu-id="7c2b5-109">Modul není vhodné používat po toto volání.</span><span class="sxs-lookup"><span data-stu-id="7c2b5-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c2b5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c2b5-110">Requirements</span></span>  
 <span data-ttu-id="7c2b5-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2b5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2b5-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c2b5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c2b5-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c2b5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c2b5-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2b5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c2b5-115">See Also</span></span>  
 [<span data-ttu-id="7c2b5-116">LoadModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7c2b5-116">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)  
 [<span data-ttu-id="7c2b5-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c2b5-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
