---
title: "ICLRMemoryNotificationCallback – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b998f8af2c7f4add3ecbb905928b5956409bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="c2c44-102">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2c44-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="c2c44-103">Umožňuje hostiteli, aby podmínky přetížení paměti sestavy pomocí podobná Win32 přístup `CreateMemoryResourceNotification` funkce.</span><span class="sxs-lookup"><span data-stu-id="c2c44-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2c44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c2c44-104">Methods</span></span>  
  
|<span data-ttu-id="c2c44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c2c44-105">Method</span></span>|<span data-ttu-id="c2c44-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2c44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2c44-107">Onmemorynotification – metoda</span><span class="sxs-lookup"><span data-stu-id="c2c44-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="c2c44-108">Modul CLR (CLR) upozorní zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="c2c44-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2c44-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2c44-109">Remarks</span></span>  
 <span data-ttu-id="c2c44-110">Hostitel používá `ICLRMemoryNotificationCallback` rozhraní můžete požádat, aby modulu CLR uvolněte paměťové prostředky.</span><span class="sxs-lookup"><span data-stu-id="c2c44-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c44-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2c44-111">Requirements</span></span>  
 <span data-ttu-id="c2c44-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c44-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c44-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2c44-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2c44-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2c44-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2c44-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c44-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c44-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2c44-116">See Also</span></span>  
 [<span data-ttu-id="c2c44-117">Ihostmemorymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2c44-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="c2c44-118">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="c2c44-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
