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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55463985a7ac93bf0ec3cda92f91f8a326f92406
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410560"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="f8cfb-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="f8cfb-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="f8cfb-103">Obsahuje hodnoty, které označují množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="f8cfb-104">Tyto hodnoty logicky mapování na události pro vysoké a nízké je paměť vrácena z `CreateMemoryResourceNotification` funkce v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8cfb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8cfb-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="f8cfb-106">Členové</span><span class="sxs-lookup"><span data-stu-id="f8cfb-106">Members</span></span>  
  
|<span data-ttu-id="f8cfb-107">Člen</span><span class="sxs-lookup"><span data-stu-id="f8cfb-107">Member</span></span>|<span data-ttu-id="f8cfb-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f8cfb-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="f8cfb-109">Dostatek fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="f8cfb-110">Velmi malé fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="f8cfb-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8cfb-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8cfb-112">Remarks</span></span>  
 <span data-ttu-id="f8cfb-113">Tato hodnota je registrem hostitele tak, aby modul CLR (CLR) podle pomocí volání [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f8cfb-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8cfb-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8cfb-114">Requirements</span></span>  
 <span data-ttu-id="f8cfb-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8cfb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8cfb-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8cfb-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8cfb-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8cfb-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8cfb-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8cfb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cfb-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8cfb-119">See also</span></span>
- [<span data-ttu-id="f8cfb-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="f8cfb-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
