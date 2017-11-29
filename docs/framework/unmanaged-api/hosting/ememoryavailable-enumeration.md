---
title: "EMemoryAvailable – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="2ed52-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="2ed52-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="2ed52-103">Obsahuje hodnoty, které označují množství volného fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="2ed52-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="2ed52-104">Tyto hodnoty logicky mapování na události pro maximální a minimální paměti vrácená z `CreateMemoryResourceNotification` funkce v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="2ed52-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed52-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ed52-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="2ed52-106">Členové</span><span class="sxs-lookup"><span data-stu-id="2ed52-106">Members</span></span>  
  
|<span data-ttu-id="2ed52-107">Člen</span><span class="sxs-lookup"><span data-stu-id="2ed52-107">Member</span></span>|<span data-ttu-id="2ed52-108">Popis</span><span class="sxs-lookup"><span data-stu-id="2ed52-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="2ed52-109">Množství fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2ed52-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="2ed52-110">Velmi malé fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2ed52-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="2ed52-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="2ed52-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ed52-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ed52-112">Remarks</span></span>  
 <span data-ttu-id="2ed52-113">Tato hodnota je předaná hostitele do common language runtime (CLR) podle pomocí volání do [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="2ed52-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ed52-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ed52-114">Requirements</span></span>  
 <span data-ttu-id="2ed52-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ed52-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ed52-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ed52-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ed52-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ed52-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ed52-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed52-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed52-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ed52-119">See Also</span></span>  
 [<span data-ttu-id="2ed52-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="2ed52-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
