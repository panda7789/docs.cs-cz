---
title: IDebuggerThreadControl – rozhraní
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 619a28d2382aa9cc3130a3130c07fa1e283119e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437912"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="fdd3b-102">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdd3b-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="fdd3b-103">Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken ladění služby.</span><span class="sxs-lookup"><span data-stu-id="fdd3b-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdd3b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fdd3b-104">Methods</span></span>  
  
|<span data-ttu-id="fdd3b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fdd3b-105">Method</span></span>|<span data-ttu-id="fdd3b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdd3b-107">ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd3b-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="fdd3b-108">Upozorní hostitele, který podproces, který odesílá tento zpětné volání je o blok v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="fdd3b-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="fdd3b-109">ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd3b-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="fdd3b-110">Upozorní hostitele, zda chcete uvolnit všechny vláken, která jsou blokovaná jsou ladění služby.</span><span class="sxs-lookup"><span data-stu-id="fdd3b-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="fdd3b-111">StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="fdd3b-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="fdd3b-112">Upozorní hostitele, že ladění služby se chystáte se spustit blokování všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="fdd3b-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fdd3b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdd3b-113">Requirements</span></span>  
 <span data-ttu-id="fdd3b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd3b-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fdd3b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdd3b-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdd3b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdd3b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd3b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdd3b-118">See Also</span></span>  
 [<span data-ttu-id="fdd3b-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="fdd3b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
