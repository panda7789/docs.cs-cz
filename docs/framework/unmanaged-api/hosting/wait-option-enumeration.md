---
title: "WAIT_OPTION – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAIT_OPTION
api_location: mscoree.dll
api_type: COM
f1_keywords: WAIT_OPTION
helpviewer_keywords: WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08bdfc928c56d144f50399814a81795fea74574a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="c9351-102">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="c9351-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="c9351-103">Obsahuje hodnoty, které označují, že akce hostitele by měl trvat, pokud operace požadoval běžné bloky runtime (CLR) jazyk.</span><span class="sxs-lookup"><span data-stu-id="c9351-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9351-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9351-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="c9351-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c9351-105">Members</span></span>  
  
|<span data-ttu-id="c9351-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c9351-106">Member</span></span>|<span data-ttu-id="c9351-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c9351-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="c9351-108">Hostitele upozorní, že úloha se probudí, modul CLR volá-li [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c9351-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="c9351-109">Zprávy v aktuální vlákno operačního systému se musí čerpadla, když se stane zablokuje vlákno upozorní hostitele.</span><span class="sxs-lookup"><span data-stu-id="c9351-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="c9351-110">Modul runtime určuje jenom na tuto hodnotu <xref:System.Threading.ApartmentState.STA> přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="c9351-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="c9351-111">Upozorní hostitele, že žádost o synchronizaci zadaný nelze rozdělit hostitele.</span><span class="sxs-lookup"><span data-stu-id="c9351-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="c9351-112">To znamená, nemůže vrátit hostitele `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="c9351-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9351-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9351-113">Remarks</span></span>  
 <span data-ttu-id="c9351-114">[Ihosttaskmanager::Sleep –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) a [ihosttaskmanager::switchtotask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody obou přijímají parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="c9351-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9351-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9351-115">Requirements</span></span>  
 <span data-ttu-id="c9351-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9351-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9351-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c9351-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9351-118">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9351-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9351-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9351-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9351-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9351-120">See Also</span></span>  
 [<span data-ttu-id="c9351-121">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="c9351-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
