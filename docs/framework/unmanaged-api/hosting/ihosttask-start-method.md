---
title: "IHostTask::Start – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1a289099245228b8806639cb98f579bc56317b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="e23a5-102">IHostTask::Start – metoda</span><span class="sxs-lookup"><span data-stu-id="e23a5-102">IHostTask::Start Method</span></span>
<span data-ttu-id="e23a5-103">Požadavky, že hostitel move – úloha reprezentována aktuální [ihosttask –](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance z pozastavenou za provozu stavu, ve kterém můžete spustit kód.</span><span class="sxs-lookup"><span data-stu-id="e23a5-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e23a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e23a5-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e23a5-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e23a5-105">Return Value</span></span>  
  
|<span data-ttu-id="e23a5-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e23a5-106">HRESULT</span></span>|<span data-ttu-id="e23a5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e23a5-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e23a5-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e23a5-108">S_OK</span></span>|<span data-ttu-id="e23a5-109">Spuštění úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e23a5-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="e23a5-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e23a5-110">E_FAIL</span></span>|<span data-ttu-id="e23a5-111">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e23a5-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e23a5-112">Když se metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e23a5-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="e23a5-113">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e23a5-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e23a5-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e23a5-114">Remarks</span></span>  
 <span data-ttu-id="e23a5-115">`Start`vždy vrátí hodnotu HRESULT S_OK, s výjimkou v případech, kde došlo k závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="e23a5-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23a5-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e23a5-116">Requirements</span></span>  
 <span data-ttu-id="e23a5-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e23a5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23a5-118">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e23a5-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e23a5-119">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e23a5-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e23a5-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23a5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="e23a5-121">See Also</span></span>  
 [<span data-ttu-id="e23a5-122">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23a5-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e23a5-123">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23a5-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e23a5-124">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23a5-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e23a5-125">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e23a5-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
