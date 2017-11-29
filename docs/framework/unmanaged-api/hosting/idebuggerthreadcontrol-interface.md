---
title: "IDebuggerThreadControl – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IDebuggerThreadControl
helpviewer_keywords: IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e3f8d04a47607958ff5d439b501a6de9bbc5b02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="c963b-102">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c963b-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="c963b-103">Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken ladění služby.</span><span class="sxs-lookup"><span data-stu-id="c963b-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c963b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c963b-104">Methods</span></span>  
  
|<span data-ttu-id="c963b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c963b-105">Method</span></span>|<span data-ttu-id="c963b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c963b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c963b-107">Threadisblockingfordebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="c963b-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="c963b-108">Upozorní hostitele, který podproces, který odesílá tento zpětné volání je o blok v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="c963b-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="c963b-109">Releaseallruntimethreads – metoda</span><span class="sxs-lookup"><span data-stu-id="c963b-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="c963b-110">Upozorní hostitele, zda chcete uvolnit všechny vláken, která jsou blokovaná jsou ladění služby.</span><span class="sxs-lookup"><span data-stu-id="c963b-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="c963b-111">Startblockingfordebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="c963b-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="c963b-112">Upozorní hostitele, že ladění služby se chystáte se spustit blokování všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="c963b-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c963b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c963b-113">Requirements</span></span>  
 <span data-ttu-id="c963b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c963b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c963b-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c963b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c963b-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c963b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c963b-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c963b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c963b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c963b-118">See Also</span></span>  
 [<span data-ttu-id="c963b-119">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="c963b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
