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
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967827"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="9a1ab-102">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a1ab-102">IHostCrst Interface</span></span>
<span data-ttu-id="9a1ab-103">Slouží jako hostitele reprezentace kritický oddíl pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a1ab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a1ab-104">Methods</span></span>  
  
|<span data-ttu-id="9a1ab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a1ab-105">Method</span></span>|<span data-ttu-id="9a1ab-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9a1ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a1ab-107">Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="9a1ab-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="9a1ab-108">Zadá kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="9a1ab-109">Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="9a1ab-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="9a1ab-110">Ponechá kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="9a1ab-111">SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="9a1ab-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="9a1ab-112">Nastaví počet typu číselník pro kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="9a1ab-113">TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="9a1ab-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="9a1ab-114">Pokusy o zadání kritický oddíl a sestavy úspěch nebo neúspěch okamžitě.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a1ab-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a1ab-115">Remarks</span></span>  
 <span data-ttu-id="9a1ab-116">`IHostCrst` Umožňuje common language runtime (CLR) přímo komunikovat s hostitele reprezentace kritický oddíl, namísto funkce Win32 `EnterCriticalSection` nebo `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="9a1ab-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1ab-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a1ab-117">Requirements</span></span>  
 <span data-ttu-id="9a1ab-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1ab-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1ab-119">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a1ab-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a1ab-120">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a1ab-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a1ab-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1ab-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a1ab-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a1ab-122">See also</span></span>

- [<span data-ttu-id="9a1ab-123">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a1ab-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="9a1ab-124">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a1ab-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="9a1ab-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9a1ab-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
