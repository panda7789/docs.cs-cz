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
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133163"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="d3ebd-102">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3ebd-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="d3ebd-103">Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.</span><span class="sxs-lookup"><span data-stu-id="d3ebd-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3ebd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d3ebd-104">Methods</span></span>  
  
|<span data-ttu-id="d3ebd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d3ebd-105">Method</span></span>|<span data-ttu-id="d3ebd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d3ebd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3ebd-107">ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="d3ebd-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="d3ebd-108">Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="d3ebd-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="d3ebd-109">ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="d3ebd-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="d3ebd-110">Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="d3ebd-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="d3ebd-111">StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="d3ebd-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="d3ebd-112">Upozorňuje hostitele, že se chystá služby ladění zahájit blokování všech vláken.</span><span class="sxs-lookup"><span data-stu-id="d3ebd-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3ebd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3ebd-113">Requirements</span></span>  
 <span data-ttu-id="d3ebd-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3ebd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ebd-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3ebd-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3ebd-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3ebd-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3ebd-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ebd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ebd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3ebd-118">See also</span></span>

- [<span data-ttu-id="d3ebd-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d3ebd-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
