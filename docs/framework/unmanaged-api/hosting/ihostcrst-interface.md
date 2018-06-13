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
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438916"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="d8d01-102">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8d01-102">IHostCrst Interface</span></span>
<span data-ttu-id="d8d01-103">Slouží jako reprezentace hostitele kritické oddílu pro dělení na vlákna.</span><span class="sxs-lookup"><span data-stu-id="d8d01-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8d01-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d8d01-104">Methods</span></span>  
  
|<span data-ttu-id="d8d01-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d8d01-105">Method</span></span>|<span data-ttu-id="d8d01-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d8d01-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8d01-107">Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="d8d01-107">Enter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|<span data-ttu-id="d8d01-108">Zadá kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="d8d01-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="d8d01-109">Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="d8d01-109">Leave Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|<span data-ttu-id="d8d01-110">Ponechá kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="d8d01-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="d8d01-111">SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="d8d01-111">SetSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|<span data-ttu-id="d8d01-112">Nastaví počet typu číselník pro kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="d8d01-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="d8d01-113">TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="d8d01-113">TryEnter Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|<span data-ttu-id="d8d01-114">Pokusí se okamžitě zadejte kritická sekce a sestavy úspěšná nebo neúspěšná.</span><span class="sxs-lookup"><span data-stu-id="d8d01-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8d01-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8d01-115">Remarks</span></span>  
 <span data-ttu-id="d8d01-116">`IHostCrst` umožňuje modul CLR (CLR) a komunikovat přímo s hostitele reprezentace kritické oddílu, nikoli pomocí Win32 funkce, jako třeba `EnterCriticalSection` nebo `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="d8d01-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8d01-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8d01-117">Requirements</span></span>  
 <span data-ttu-id="d8d01-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8d01-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8d01-119">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8d01-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8d01-120">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8d01-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8d01-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8d01-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8d01-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8d01-122">See Also</span></span>  
 [<span data-ttu-id="d8d01-123">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8d01-123">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d8d01-124">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8d01-124">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="d8d01-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d8d01-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
