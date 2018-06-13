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
ms.openlocfilehash: 139cf540617e278eeaae8a2a5acf10dd797d5d10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429883"
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="d3d1a-102">EMemoryAvailable – výčet</span><span class="sxs-lookup"><span data-stu-id="d3d1a-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="d3d1a-103">Obsahuje hodnoty, které označují množství volného fyzické paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="d3d1a-104">Tyto hodnoty logicky mapování na události pro maximální a minimální paměti vrácená z `CreateMemoryResourceNotification` funkce v rozhraní API Win32.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3d1a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3d1a-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="d3d1a-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d3d1a-106">Members</span></span>  
  
|<span data-ttu-id="d3d1a-107">Člen</span><span class="sxs-lookup"><span data-stu-id="d3d1a-107">Member</span></span>|<span data-ttu-id="d3d1a-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d3d1a-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="d3d1a-109">Množství fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="d3d1a-110">Velmi malé fyzické paměti je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="d3d1a-111">Dostupná fyzická paměť je neutrální.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d1a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3d1a-112">Remarks</span></span>  
 <span data-ttu-id="d3d1a-113">Tato hodnota je předaná hostitele do common language runtime (CLR) podle pomocí volání do [iclrmemorynotificationcallback::onmemorynotification –](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="d3d1a-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d1a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3d1a-114">Requirements</span></span>  
 <span data-ttu-id="d3d1a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d1a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d1a-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3d1a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3d1a-117">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3d1a-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3d1a-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d1a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3d1a-119">See Also</span></span>  
 [<span data-ttu-id="d3d1a-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="d3d1a-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
