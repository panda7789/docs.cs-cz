---
title: "IHostTask::Start – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db43ec56fac86b0040aa4f701940abf0d1c0df07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="7b7ae-102">IHostTask::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="7b7ae-102">IHostTask::Start Method</span></span>
<span data-ttu-id="7b7ae-103">Požadavky, že hostitel move – úloha reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance z pozastavenou za provozu stavu, ve kterém můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b7ae-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7b7ae-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7b7ae-105">Return Value</span></span>  
  
|<span data-ttu-id="7b7ae-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b7ae-106">HRESULT</span></span>|<span data-ttu-id="7b7ae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b7ae-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b7ae-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b7ae-108">S_OK</span></span>|<span data-ttu-id="7b7ae-109">Spuštění úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="7b7ae-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b7ae-110">E_FAIL</span></span>|<span data-ttu-id="7b7ae-111">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b7ae-112">Když se metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="7b7ae-113">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b7ae-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b7ae-114">Remarks</span></span>  
 <span data-ttu-id="7b7ae-115">`Start`vždy vrátí hodnotu HRESULT S_OK, s výjimkou v případech, kde došlo k závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="7b7ae-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7ae-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b7ae-116">Requirements</span></span>  
 <span data-ttu-id="7b7ae-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b7ae-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7ae-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b7ae-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b7ae-119">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b7ae-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b7ae-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7ae-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7ae-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b7ae-121">See Also</span></span>  
 [<span data-ttu-id="7b7ae-122">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b7ae-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7b7ae-123">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b7ae-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7b7ae-124">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b7ae-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7b7ae-125">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b7ae-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
