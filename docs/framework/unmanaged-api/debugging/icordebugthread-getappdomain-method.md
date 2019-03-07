---
title: ICorDebugThread::GetAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a37ee8367006975b0f8ee4fa638ae3d72f9486
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487743"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="ab59f-102">ICorDebugThread::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="ab59f-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="ab59f-103">Získá ukazatel rozhraní aplikační doménu, ve kterém tento ICorDebugThread právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="ab59f-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab59f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab59f-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab59f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab59f-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="ab59f-106">[out] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve kterém je aktuálně spuštěno toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="ab59f-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab59f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab59f-107">Requirements</span></span>  
 <span data-ttu-id="ab59f-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab59f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab59f-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab59f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab59f-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab59f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab59f-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab59f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
