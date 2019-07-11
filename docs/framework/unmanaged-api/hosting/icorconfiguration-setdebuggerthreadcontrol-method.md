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
ms.openlocfilehash: ebbc076f52c661a394eff51954fceefe8e439ded
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779893"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="1e9ef-102">ICorConfiguration::SetDebuggerThreadControl – metoda</span><span class="sxs-lookup"><span data-stu-id="1e9ef-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="1e9ef-103">Nastaví rozhraní zpětného volání, která služeb ladění bude volat common language runtime (CLR) vlákna jsou blokované a odblokováno pro ladění.</span><span class="sxs-lookup"><span data-stu-id="1e9ef-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e9ef-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e9ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e9ef-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="1e9ef-106">[in] Ukazatel [idebuggerthreadcontrol –](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) objektu, která upozorňuje hostitele o blokování a odblokování vláken pomocí služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="1e9ef-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e9ef-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e9ef-107">Requirements</span></span>  
 <span data-ttu-id="1e9ef-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e9ef-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e9ef-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e9ef-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e9ef-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e9ef-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e9ef-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e9ef-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9ef-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e9ef-112">See also</span></span>

- [<span data-ttu-id="1e9ef-113">ICorConfiguration – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e9ef-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
