---
title: EMemoryAvailable – výčet
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176432"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="bb9de-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="bb9de-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="bb9de-103">Obsahuje hodnoty, které označují množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="bb9de-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="bb9de-104">Tyto hodnoty logicky mapovat na události pro `CreateMemoryResourceNotification` vysoké a nedostatku paměti vrácené z funkce v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bb9de-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb9de-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="bb9de-106">Členové</span><span class="sxs-lookup"><span data-stu-id="bb9de-106">Members</span></span>  
  
|<span data-ttu-id="bb9de-107">Člen</span><span class="sxs-lookup"><span data-stu-id="bb9de-107">Member</span></span>|<span data-ttu-id="bb9de-108">Popis</span><span class="sxs-lookup"><span data-stu-id="bb9de-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="bb9de-109">K dispozici je spousta fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="bb9de-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="bb9de-110">Je k dispozici velmi málo fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="bb9de-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="bb9de-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="bb9de-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb9de-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb9de-112">Remarks</span></span>  
 <span data-ttu-id="bb9de-113">Tato hodnota je předána hostitelem cltime jazyka společného jazyka pomocí volání [metody ICLRMemoryNotificationCallback::OnMemoryNotification.](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)</span><span class="sxs-lookup"><span data-stu-id="bb9de-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb9de-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb9de-114">Requirements</span></span>  
 <span data-ttu-id="bb9de-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb9de-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb9de-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb9de-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb9de-117">**Knihovna:** Soubor MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb9de-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb9de-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb9de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9de-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb9de-119">See also</span></span>

- [<span data-ttu-id="bb9de-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="bb9de-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
