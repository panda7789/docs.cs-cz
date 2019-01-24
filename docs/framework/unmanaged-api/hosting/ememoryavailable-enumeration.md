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
ms.openlocfilehash: f0ffb85dc5f321e45432d6c2fa9448919957f0e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665198"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="30a18-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="30a18-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="30a18-103">Obsahuje hodnoty, které označují množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="30a18-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="30a18-104">Tyto hodnoty logicky mapování na události pro vysoké a nízké je paměť vrácena z `CreateMemoryResourceNotification` – funkce rozhraní Win32 API.</span><span class="sxs-lookup"><span data-stu-id="30a18-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a18-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30a18-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="30a18-106">Členové</span><span class="sxs-lookup"><span data-stu-id="30a18-106">Members</span></span>  
  
|<span data-ttu-id="30a18-107">Člen</span><span class="sxs-lookup"><span data-stu-id="30a18-107">Member</span></span>|<span data-ttu-id="30a18-108">Popis</span><span class="sxs-lookup"><span data-stu-id="30a18-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="30a18-109">Dostatek fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30a18-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="30a18-110">Velmi malé fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="30a18-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="30a18-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="30a18-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30a18-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30a18-112">Remarks</span></span>  
 <span data-ttu-id="30a18-113">Tato hodnota je registrem hostitele tak, aby modul CLR (CLR) podle pomocí volání [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="30a18-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30a18-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30a18-114">Requirements</span></span>  
 <span data-ttu-id="30a18-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30a18-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30a18-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30a18-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30a18-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30a18-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30a18-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30a18-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a18-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30a18-119">See also</span></span>
- [<span data-ttu-id="30a18-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="30a18-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
