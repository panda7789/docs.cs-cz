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
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703799"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="27cf3-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27cf3-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="27cf3-103">Umožňuje hostiteli hlásit podmínky pro tlak paměti pomocí přístupu podobného `CreateMemoryResourceNotification` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="27cf3-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27cf3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27cf3-104">Methods</span></span>  
  
|<span data-ttu-id="27cf3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27cf3-105">Method</span></span>|<span data-ttu-id="27cf3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="27cf3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27cf3-107">OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="27cf3-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="27cf3-108">Upozorňuje modul CLR (Common Language Runtime) na zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="27cf3-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27cf3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27cf3-109">Remarks</span></span>  
 <span data-ttu-id="27cf3-110">Hostitel používá `ICLRMemoryNotificationCallback` rozhraní k vyžádání prostředků volné paměti CLR.</span><span class="sxs-lookup"><span data-stu-id="27cf3-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27cf3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27cf3-111">Requirements</span></span>  
 <span data-ttu-id="27cf3-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27cf3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27cf3-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27cf3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27cf3-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27cf3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27cf3-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27cf3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cf3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="27cf3-116">See also</span></span>

- [<span data-ttu-id="27cf3-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27cf3-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="27cf3-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="27cf3-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
