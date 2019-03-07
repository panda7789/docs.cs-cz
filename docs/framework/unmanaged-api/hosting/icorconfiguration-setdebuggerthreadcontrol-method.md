---
title: ICorConfiguration::SetDebuggerThreadControl – metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cecbbd7509fcd4f79aeb6e2711e8b7604c2f3a9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489686"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="3b6cf-102">ICorConfiguration::SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="3b6cf-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="3b6cf-103">Nastaví rozhraní zpětného volání, která služeb ladění bude volat common language runtime (CLR) vlákna jsou blokované a odblokováno pro ladění.</span><span class="sxs-lookup"><span data-stu-id="3b6cf-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b6cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b6cf-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b6cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b6cf-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="3b6cf-106">[in] Ukazatel [idebuggerthreadcontrol –](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) objektu, která upozorňuje hostitele o blokování a odblokování vláken pomocí služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="3b6cf-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b6cf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b6cf-107">Requirements</span></span>  
 <span data-ttu-id="3b6cf-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b6cf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b6cf-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3b6cf-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b6cf-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b6cf-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b6cf-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b6cf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6cf-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b6cf-112">See also</span></span>
- [<span data-ttu-id="3b6cf-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b6cf-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
