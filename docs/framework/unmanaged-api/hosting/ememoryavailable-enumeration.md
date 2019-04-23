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
ms.openlocfilehash: d98a0c1c3187b81c44fae6eee91d975169a40045
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072802"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="52391-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="52391-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="52391-103">Obsahuje hodnoty, které označují množství volné fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="52391-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="52391-104">Tyto hodnoty logicky mapování na události pro vysoké a nízké je paměť vrácena z `CreateMemoryResourceNotification` funkce v rozhraní Windows API.</span><span class="sxs-lookup"><span data-stu-id="52391-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Windows API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52391-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52391-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="52391-106">Členové</span><span class="sxs-lookup"><span data-stu-id="52391-106">Members</span></span>  
  
|<span data-ttu-id="52391-107">Člen</span><span class="sxs-lookup"><span data-stu-id="52391-107">Member</span></span>|<span data-ttu-id="52391-108">Popis</span><span class="sxs-lookup"><span data-stu-id="52391-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="52391-109">Dostatek fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="52391-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="52391-110">Velmi malé fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="52391-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="52391-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="52391-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52391-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52391-112">Remarks</span></span>  
 <span data-ttu-id="52391-113">Tato hodnota je registrem hostitele tak, aby modul CLR (CLR) podle pomocí volání [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="52391-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52391-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52391-114">Requirements</span></span>  
 <span data-ttu-id="52391-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52391-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52391-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52391-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52391-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52391-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52391-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52391-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52391-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52391-119">See also</span></span>

- [<span data-ttu-id="52391-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="52391-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
