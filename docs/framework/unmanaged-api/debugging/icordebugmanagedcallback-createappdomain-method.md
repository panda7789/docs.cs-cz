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
ms.openlocfilehash: afd8bd76f8d738c9eaa3a8e3d490e175e408b92b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204299"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="6b6b0-102">ICorDebugManagedCallback::CreateAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="6b6b0-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="6b6b0-103">Upozorní ladicího programu, že se vytvořila domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b6b0-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b6b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b6b0-104">Syntax</span></span>  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b6b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b6b0-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="6b6b0-106">[in] Ukazatel na objekt ICorDebugProcess, který představuje proces, ve kterém byla vytvořena domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b6b0-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="6b6b0-107">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, který byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="6b6b0-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b6b0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b6b0-108">Requirements</span></span>  
 <span data-ttu-id="6b6b0-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b6b0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b6b0-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b6b0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b6b0-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b6b0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b6b0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b6b0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6b0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b6b0-113">See also</span></span>

- [<span data-ttu-id="6b6b0-114">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b6b0-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
