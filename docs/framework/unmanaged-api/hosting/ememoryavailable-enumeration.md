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
ms.openlocfilehash: aec3c5f140df7eab10ea2bfa33634a4d853adcb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134294"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="c3020-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="c3020-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="c3020-103">Obsahuje hodnoty, které udávají množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="c3020-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="c3020-104">Tyto hodnoty logicky mapují na události pro vysokou a nízkou paměť vrácenou funkcí `CreateMemoryResourceNotification` v rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c3020-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3020-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3020-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="c3020-106">Členové</span><span class="sxs-lookup"><span data-stu-id="c3020-106">Members</span></span>  
  
|<span data-ttu-id="c3020-107">Člen</span><span class="sxs-lookup"><span data-stu-id="c3020-107">Member</span></span>|<span data-ttu-id="c3020-108">Popis</span><span class="sxs-lookup"><span data-stu-id="c3020-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="c3020-109">K dispozici je dostatek fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="c3020-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="c3020-110">K dispozici je jen málo fyzické paměti.</span><span class="sxs-lookup"><span data-stu-id="c3020-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="c3020-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="c3020-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3020-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3020-112">Remarks</span></span>  
 <span data-ttu-id="c3020-113">Tato hodnota je předána hostitelem do modulu CLR (Common Language Runtime) pomocí volání metody [ICLRMemoryNotificationCallback –:: OnMemoryNotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c3020-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3020-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3020-114">Requirements</span></span>  
 <span data-ttu-id="c3020-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3020-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3020-116">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c3020-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c3020-117">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3020-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3020-118">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3020-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3020-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3020-119">See also</span></span>

- [<span data-ttu-id="c3020-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="c3020-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
