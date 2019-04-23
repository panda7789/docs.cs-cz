---
title: IHostAutoEvent – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb5fea403f8210ea93d240aa3aabd4325524b987
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080940"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="294f8-102">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="294f8-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="294f8-103">Poskytuje reprezentaci hostitele implementace události automatického obnovení.</span><span class="sxs-lookup"><span data-stu-id="294f8-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="294f8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="294f8-104">Methods</span></span>  
  
|<span data-ttu-id="294f8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="294f8-105">Method</span></span>|<span data-ttu-id="294f8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="294f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="294f8-107">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="294f8-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="294f8-108">Nastaví aktuální `IHostAutoEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="294f8-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="294f8-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="294f8-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="294f8-110">Způsobí, že aktuální `IHostAutoEvent` instance počkat, až vlastní události nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="294f8-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="294f8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="294f8-111">Requirements</span></span>  
 <span data-ttu-id="294f8-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="294f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="294f8-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="294f8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="294f8-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="294f8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="294f8-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="294f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="294f8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="294f8-116">See also</span></span>

- [<span data-ttu-id="294f8-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="294f8-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="294f8-118">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="294f8-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="294f8-119">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="294f8-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="294f8-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="294f8-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
