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
ms.openlocfilehash: 822396e28d000a5309738680fec502e1aeacd67c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616213"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="107e3-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="107e3-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="107e3-103">Obsahuje hodnoty, které udávají množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="107e3-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="107e3-104">Tyto hodnoty logicky mapují na události pro vysokou a nízkou paměť vrácenou `CreateMemoryResourceNotification` funkcí v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="107e3-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="107e3-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="107e3-106">Členové</span><span class="sxs-lookup"><span data-stu-id="107e3-106">Members</span></span>  
  
|<span data-ttu-id="107e3-107">Člen</span><span class="sxs-lookup"><span data-stu-id="107e3-107">Member</span></span>|<span data-ttu-id="107e3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="107e3-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="107e3-109">K dispozici je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="107e3-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="107e3-110">K dispozici je jen málo fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="107e3-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="107e3-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="107e3-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107e3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="107e3-112">Remarks</span></span>  
 <span data-ttu-id="107e3-113">Tato hodnota je předána hostitelem do modulu CLR (Common Language Runtime) pomocí volání metody [ICLRMemoryNotificationCallback –:: OnMemoryNotification –](iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="107e3-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107e3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="107e3-114">Requirements</span></span>  
 <span data-ttu-id="107e3-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="107e3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107e3-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="107e3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="107e3-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="107e3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="107e3-118">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107e3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107e3-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="107e3-119">See also</span></span>

- [<span data-ttu-id="107e3-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="107e3-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
