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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431516"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="bb748-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb748-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="bb748-103">Umožňuje hostiteli, aby podmínky přetížení paměti sestavy pomocí podobná Win32 přístup `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="bb748-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb748-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bb748-104">Methods</span></span>  
  
|<span data-ttu-id="bb748-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bb748-105">Method</span></span>|<span data-ttu-id="bb748-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bb748-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb748-107">OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="bb748-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="bb748-108">Modul CLR (CLR) upozorní zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="bb748-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb748-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb748-109">Remarks</span></span>  
 <span data-ttu-id="bb748-110">Hostitel používá `ICLRMemoryNotificationCallback` rozhraní můžete požádat, aby modulu CLR uvolněte paměťové prostředky.</span><span class="sxs-lookup"><span data-stu-id="bb748-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb748-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb748-111">Requirements</span></span>  
 <span data-ttu-id="bb748-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb748-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb748-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb748-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb748-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb748-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb748-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb748-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb748-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb748-116">See Also</span></span>  
 [<span data-ttu-id="bb748-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb748-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="bb748-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bb748-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
