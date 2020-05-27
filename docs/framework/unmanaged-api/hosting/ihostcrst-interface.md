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
ms.openlocfilehash: e8cb1486ccea11ba6edcf7bbb781a9bf210b496d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804905"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="c238f-102">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c238f-102">IHostCrst Interface</span></span>
<span data-ttu-id="c238f-103">Slouží jako reprezentace kritické části pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="c238f-103">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c238f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c238f-104">Methods</span></span>  
  
|<span data-ttu-id="c238f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-105">Method</span></span>|<span data-ttu-id="c238f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c238f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c238f-107">Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-107">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="c238f-108">Vstupuje do kritické části.</span><span class="sxs-lookup"><span data-stu-id="c238f-108">Enters the critical section.</span></span>|  
|[<span data-ttu-id="c238f-109">Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-109">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="c238f-110">Ponechá oddíl kritické.</span><span class="sxs-lookup"><span data-stu-id="c238f-110">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="c238f-111">SetSpinCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-111">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="c238f-112">Nastaví počet číselníků pro kritickou část.</span><span class="sxs-lookup"><span data-stu-id="c238f-112">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="c238f-113">TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="c238f-113">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="c238f-114">Pokusí se zadat kritickou část a okamžitě nahlásit úspěšnost nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="c238f-114">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c238f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c238f-115">Remarks</span></span>  
 <span data-ttu-id="c238f-116">`IHostCrst`umožňuje modulu CLR (Common Language Runtime) komunikovat přímo s reprezentací hostitele kritické sekce místo použití funkcí Win32, jako je například `EnterCriticalSection` nebo `LeaveCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="c238f-116">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c238f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c238f-117">Requirements</span></span>  
 <span data-ttu-id="c238f-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c238f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c238f-119">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c238f-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c238f-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c238f-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c238f-121">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c238f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c238f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c238f-122">See also</span></span>

- [<span data-ttu-id="c238f-123">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c238f-123">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c238f-124">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c238f-124">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="c238f-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c238f-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
