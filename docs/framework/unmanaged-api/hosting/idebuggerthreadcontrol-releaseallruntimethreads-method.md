---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 136dab5c05c310d85a5e18bcdc6da0de901d3ace
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227467"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="c31b6-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c31b6-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="c31b6-103">Upozorňuje hostitele, že ladění služby se chystáte uvolnit všechna vlákna, které jsou blokovány.</span><span class="sxs-lookup"><span data-stu-id="c31b6-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c31b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c31b6-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c31b6-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c31b6-105">Remarks</span></span>  
 <span data-ttu-id="c31b6-106">`ReleaseAllRuntimeThreads` Ve vlákně modulu runtime nebude nikdy volána metoda.</span><span class="sxs-lookup"><span data-stu-id="c31b6-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="c31b6-107">Pokud má hostitel modulu runtime vlákno blokované, to by měla uvolnit ji nyní.</span><span class="sxs-lookup"><span data-stu-id="c31b6-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c31b6-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c31b6-108">Requirements</span></span>  
 <span data-ttu-id="c31b6-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c31b6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c31b6-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c31b6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c31b6-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c31b6-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c31b6-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c31b6-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c31b6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c31b6-113">See also</span></span>

- [<span data-ttu-id="c31b6-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c31b6-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
