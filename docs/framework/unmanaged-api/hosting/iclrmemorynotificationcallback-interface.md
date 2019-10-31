---
title: ICLRMemoryNotificationCallback – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140999"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="01468-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01468-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="01468-103">Umožňuje hostiteli hlásit podmínky pro tlak paměti pomocí přístupu podobného funkci Win32 `CreateMemoryResourceNotification`.</span><span class="sxs-lookup"><span data-stu-id="01468-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01468-104">Metody</span><span class="sxs-lookup"><span data-stu-id="01468-104">Methods</span></span>  
  
|<span data-ttu-id="01468-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01468-105">Method</span></span>|<span data-ttu-id="01468-106">Popis</span><span class="sxs-lookup"><span data-stu-id="01468-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01468-107">OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="01468-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="01468-108">Upozorňuje modul CLR (Common Language Runtime) na zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="01468-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01468-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01468-109">Remarks</span></span>  
 <span data-ttu-id="01468-110">Hostitel používá rozhraní `ICLRMemoryNotificationCallback` k vyžádání prostředků volné paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="01468-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01468-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01468-111">Requirements</span></span>  
 <span data-ttu-id="01468-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01468-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01468-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01468-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01468-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01468-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01468-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01468-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01468-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01468-116">See also</span></span>

- [<span data-ttu-id="01468-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01468-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="01468-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="01468-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
