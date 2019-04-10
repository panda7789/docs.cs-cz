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
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212151"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="a8f02-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8f02-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="a8f02-103">Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí metodiky podobný Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="a8f02-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8f02-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a8f02-104">Methods</span></span>  
  
|<span data-ttu-id="a8f02-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a8f02-105">Method</span></span>|<span data-ttu-id="a8f02-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a8f02-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8f02-107">OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="a8f02-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="a8f02-108">Zatížení paměti v počítači upozorní common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a8f02-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8f02-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8f02-109">Remarks</span></span>  
 <span data-ttu-id="a8f02-110">Hostitel používá `ICLRMemoryNotificationCallback` rozhraní pro žádosti, že modul CLR uvolnění paměti prostředků.</span><span class="sxs-lookup"><span data-stu-id="a8f02-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f02-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8f02-111">Requirements</span></span>  
 <span data-ttu-id="a8f02-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8f02-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f02-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a8f02-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8f02-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8f02-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a8f02-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a8f02-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f02-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f02-116">See also</span></span>

- [<span data-ttu-id="a8f02-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8f02-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="a8f02-118">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="a8f02-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
