---
title: "IHostAutoEvent – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent
helpviewer_keywords: IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c99bde7641ee640df06be71fc43a7f8774f7ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="f8684-102">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8684-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="f8684-103">Poskytuje reprezentaci hostitele implementace události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="f8684-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8684-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f8684-104">Methods</span></span>  
  
|<span data-ttu-id="f8684-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f8684-105">Method</span></span>|<span data-ttu-id="f8684-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f8684-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8684-107">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="f8684-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="f8684-108">Nastaví aktuální `IHostAutoEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="f8684-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="f8684-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="f8684-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="f8684-110">Způsobí, že aktuální `IHostAutoEvent` instance počkal vlastní události nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="f8684-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f8684-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8684-111">Requirements</span></span>  
 <span data-ttu-id="f8684-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8684-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8684-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8684-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8684-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8684-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8684-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8684-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8684-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8684-116">See Also</span></span>  
 [<span data-ttu-id="f8684-117">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8684-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f8684-118">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8684-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="f8684-119">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8684-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="f8684-120">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="f8684-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
