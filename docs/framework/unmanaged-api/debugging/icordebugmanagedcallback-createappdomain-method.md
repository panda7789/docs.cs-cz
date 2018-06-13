---
title: ICorDebugManagedCallback::CreateAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac4b5b7a4a64a5fc939a7d35718ef276717fe7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415425"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="c8768-102">ICorDebugManagedCallback::CreateAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c8768-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="c8768-103">Upozorní ladicího programu vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8768-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8768-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8768-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8768-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8768-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="c8768-106">[v] Ukazatel na ICorDebugProcess objekt, který představuje proces, ve kterém byla vytvořena domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c8768-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c8768-107">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c8768-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8768-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8768-108">Requirements</span></span>  
 <span data-ttu-id="c8768-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8768-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8768-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8768-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8768-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8768-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8768-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8768-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8768-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8768-113">See Also</span></span>  
 [<span data-ttu-id="c8768-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8768-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
