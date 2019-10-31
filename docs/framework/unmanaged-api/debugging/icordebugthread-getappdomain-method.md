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
ms.openlocfilehash: a845eed993914e02de34ec5c60ed232ccabc561e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133531"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="4defb-102">ICorDebugThread::GetAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="4defb-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="4defb-103">Získá ukazatel rozhraní na doménu aplikace, ve které je aktuálně prováděna tato ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4defb-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4defb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4defb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4defb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4defb-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="4defb-106">mimo Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve které je aktuálně spuštěno toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="4defb-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4defb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4defb-107">Requirements</span></span>  
 <span data-ttu-id="4defb-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4defb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4defb-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4defb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4defb-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4defb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4defb-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4defb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
