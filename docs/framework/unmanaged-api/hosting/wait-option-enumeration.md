---
title: WAIT_OPTION – výčet
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
ms.openlocfilehash: 2f83bc5b114b746958f936c311efa823d88441d1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503884"
---
# <a name="wait_option-enumeration"></a><span data-ttu-id="cd800-102">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="cd800-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="cd800-103">Obsahuje hodnoty, které určují akci, kterou by měl hostitel provést, pokud je operace požadována v rámci bloků modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cd800-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd800-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="cd800-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cd800-105">Members</span></span>  
  
|<span data-ttu-id="cd800-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cd800-106">Member</span></span>|<span data-ttu-id="cd800-107">Description</span><span class="sxs-lookup"><span data-stu-id="cd800-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="cd800-108">Upozorní hostitele, že by měl být úkol probuzeny, pokud CLR volá metodu [IHostTask:: Alert](ihosttask-alert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cd800-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="cd800-109">Upozorní hostitele, že musí pumpovat zprávy v aktuálním vláknu operačního systému, pokud se vlákno zablokuje.</span><span class="sxs-lookup"><span data-stu-id="cd800-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="cd800-110">Modul runtime tuto hodnotu určuje pouze v <xref:System.Threading.ApartmentState.STA> vlákně.</span><span class="sxs-lookup"><span data-stu-id="cd800-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="cd800-111">Upozorní hostitele, že zadaný požadavek na synchronizaci nemůže být hostitelem.</span><span class="sxs-lookup"><span data-stu-id="cd800-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="cd800-112">To znamená, že hostitel nemůže vracet `HOST_E_DEADLOCK` .</span><span class="sxs-lookup"><span data-stu-id="cd800-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd800-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd800-113">Remarks</span></span>  
 <span data-ttu-id="cd800-114">Metody [IHostTaskManager:: Sleep](ihosttaskmanager-sleep-method.md) a [IHostTaskManager:: SwitchToTask –](ihosttaskmanager-switchtotask-method.md) obě přebírají parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="cd800-114">The [IHostTaskManager::Sleep](ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd800-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd800-115">Requirements</span></span>  
 <span data-ttu-id="cd800-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd800-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd800-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cd800-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd800-118">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd800-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd800-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd800-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd800-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd800-120">See also</span></span>

- [<span data-ttu-id="cd800-121">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="cd800-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
