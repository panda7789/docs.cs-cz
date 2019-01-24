---
title: IHostCrst – rozhraní
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34a911668db09b255282833cec3e6272b315373b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618656"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="2bf0f-102">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bf0f-102">IHostCrst Interface</span></span>
<span data-ttu-id="2bf0f-103">Slouží jako hostitele reprezentace kritický oddíl pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bf0f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2bf0f-104">Methods</span></span>  
  
|<span data-ttu-id="2bf0f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2bf0f-105">Method</span></span>|<span data-ttu-id="2bf0f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2bf0f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bf0f-107">Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf0f-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="2bf0f-108">Zadá kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="2bf0f-109">Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf0f-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="2bf0f-110">Ponechá kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="2bf0f-111">SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf0f-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="2bf0f-112">Nastaví počet typu číselník pro kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="2bf0f-113">TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="2bf0f-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="2bf0f-114">Pokusy o zadání kritický oddíl a sestavy úspěch nebo neúspěch okamžitě.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf0f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bf0f-115">Remarks</span></span>  
 <span data-ttu-id="2bf0f-116">`IHostCrst` Umožňuje common language runtime (CLR) přímo komunikovat s hostitele reprezentace kritický oddíl, namísto funkce Win32 `EnterCriticalSection` nebo `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="2bf0f-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bf0f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bf0f-117">Requirements</span></span>  
 <span data-ttu-id="2bf0f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bf0f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf0f-119">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2bf0f-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bf0f-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bf0f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bf0f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf0f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf0f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bf0f-122">See also</span></span>
- [<span data-ttu-id="2bf0f-123">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bf0f-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="2bf0f-124">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bf0f-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="2bf0f-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2bf0f-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
