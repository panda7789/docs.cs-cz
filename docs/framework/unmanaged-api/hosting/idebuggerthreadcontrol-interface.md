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
ms.openlocfilehash: 7a551d3cc6ab3dd3887f232018f8201de4036d1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096833"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="b2828-102">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2828-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="b2828-103">Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken pomocí služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="b2828-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2828-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2828-104">Methods</span></span>  
  
|<span data-ttu-id="b2828-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2828-105">Method</span></span>|<span data-ttu-id="b2828-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b2828-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2828-107">ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="b2828-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="b2828-108">Upozorňuje hostitele, který spočívá v vlákna, která se odesílá toto zpětné volání do bloku v rámci služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="b2828-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="b2828-109">ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="b2828-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="b2828-110">Upozorňuje hostitele, že ladění služby se chystáte uvolnit všechna vlákna, které jsou blokovány.</span><span class="sxs-lookup"><span data-stu-id="b2828-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="b2828-111">StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="b2828-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="b2828-112">Upozorňuje hostitele, spustí blokující všechna vlákna jsou ladění služby.</span><span class="sxs-lookup"><span data-stu-id="b2828-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2828-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2828-113">Requirements</span></span>  
 <span data-ttu-id="b2828-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2828-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2828-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2828-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2828-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2828-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b2828-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b2828-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b2828-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2828-118">See also</span></span>

- [<span data-ttu-id="b2828-119">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="b2828-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
