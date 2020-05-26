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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805277"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="c5cc1-102">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5cc1-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="c5cc1-103">Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5cc1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c5cc1-104">Methods</span></span>  
  
|<span data-ttu-id="c5cc1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c5cc1-105">Method</span></span>|<span data-ttu-id="c5cc1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c5cc1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5cc1-107">ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="c5cc1-107">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="c5cc1-108">Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="c5cc1-109">ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c5cc1-109">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="c5cc1-110">Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="c5cc1-111">StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="c5cc1-111">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="c5cc1-112">Upozorňuje hostitele, že se chystá služby ladění zahájit blokování všech vláken.</span><span class="sxs-lookup"><span data-stu-id="c5cc1-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5cc1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5cc1-113">Requirements</span></span>  
 <span data-ttu-id="c5cc1-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5cc1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5cc1-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c5cc1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5cc1-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5cc1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5cc1-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5cc1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5cc1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5cc1-118">See also</span></span>

- [<span data-ttu-id="c5cc1-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c5cc1-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
