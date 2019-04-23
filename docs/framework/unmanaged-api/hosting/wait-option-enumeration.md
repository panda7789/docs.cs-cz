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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ac28f28d4d284ba26fadd46e53ebeb8e5b5f3cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139578"
---
# <a name="waitoption-enumeration"></a><span data-ttu-id="8447b-102">WAIT_OPTION – výčet</span><span class="sxs-lookup"><span data-stu-id="8447b-102">WAIT_OPTION Enumeration</span></span>
<span data-ttu-id="8447b-103">Obsahuje hodnoty, které označují, že by akce hostitele zabrat Pokud operace požadoval společné bloky language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8447b-103">Contains values that indicate the action a host should take if an operation requested by the common language runtime (CLR) blocks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8447b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8447b-104">Syntax</span></span>  
  
```  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a><span data-ttu-id="8447b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8447b-105">Members</span></span>  
  
|<span data-ttu-id="8447b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8447b-106">Member</span></span>|<span data-ttu-id="8447b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8447b-107">Description</span></span>|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|<span data-ttu-id="8447b-108">Upozorňuje hostitele, že úloha se probudí, modul CLR volá-li [ihosttask::alert –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8447b-108">Notifies the host that the task should be awakened if the CLR calls the [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) method.</span></span>|  
|`WAIT_MSGPUMP`|<span data-ttu-id="8447b-109">Upozorňuje hostitele, že ho musí pump zprávy v aktuálním vlákně operačního systému, pokud vlákno bude blokováno.</span><span class="sxs-lookup"><span data-stu-id="8447b-109">Notifies the host that it must pump messages on the current OS thread if the thread becomes blocked.</span></span> <span data-ttu-id="8447b-110">Modul runtime určuje pouze na tuto hodnotu <xref:System.Threading.ApartmentState.STA> vlákna.</span><span class="sxs-lookup"><span data-stu-id="8447b-110">The runtime specifies this value only on an <xref:System.Threading.ApartmentState.STA> thread.</span></span>|  
|`WAIT_NOTINDEADLOCK`|<span data-ttu-id="8447b-111">Upozorňuje hostitele, nelze rozdělit žádost o synchronizaci zadaný hostitel.</span><span class="sxs-lookup"><span data-stu-id="8447b-111">Notifies the host that the specified synchronization request cannot be broken by a host.</span></span> <span data-ttu-id="8447b-112">To znamená, nejde vrátit hostitele `HOST_E_DEADLOCK`.</span><span class="sxs-lookup"><span data-stu-id="8447b-112">That is, the host cannot return `HOST_E_DEADLOCK`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8447b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8447b-113">Remarks</span></span>  
 <span data-ttu-id="8447b-114">[Ihosttaskmanager::Sleep –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) a [ihosttaskmanager::switchtotask –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) metody obou přijímají parametr tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="8447b-114">The [IHostTaskManager::Sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md) and [IHostTaskManager::SwitchToTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md) methods both take a parameter of this type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8447b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8447b-115">Requirements</span></span>  
 <span data-ttu-id="8447b-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8447b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8447b-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8447b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8447b-118">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8447b-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8447b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8447b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8447b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8447b-120">See also</span></span>

- [<span data-ttu-id="8447b-121">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="8447b-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
