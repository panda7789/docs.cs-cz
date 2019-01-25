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
ms.openlocfilehash: b3167d288a57575af85a9cb50f5c0cd82c8e9cc9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702792"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="1804a-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1804a-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="1804a-103">Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí metodiky podobný Win32 `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="1804a-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1804a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1804a-104">Methods</span></span>  
  
|<span data-ttu-id="1804a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1804a-105">Method</span></span>|<span data-ttu-id="1804a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1804a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1804a-107">OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="1804a-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="1804a-108">Zatížení paměti v počítači upozorní common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1804a-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1804a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1804a-109">Remarks</span></span>  
 <span data-ttu-id="1804a-110">Hostitel používá `ICLRMemoryNotificationCallback` rozhraní pro žádosti, že modul CLR uvolnění paměti prostředků.</span><span class="sxs-lookup"><span data-stu-id="1804a-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1804a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1804a-111">Requirements</span></span>  
 <span data-ttu-id="1804a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1804a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1804a-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1804a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1804a-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1804a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1804a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1804a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1804a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1804a-116">See also</span></span>
- [<span data-ttu-id="1804a-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1804a-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="1804a-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="1804a-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
