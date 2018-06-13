---
title: ICLRTask::YieldTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 821f524cc8ff7f9983f811f539e2badb2306be26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437700"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="ee3d7-102">ICLRTask::YieldTask – metoda</span><span class="sxs-lookup"><span data-stu-id="ee3d7-102">ICLRTask::YieldTask Method</span></span>
<span data-ttu-id="ee3d7-103">Požadavky, které modul CLR (CLR) uvedl z produkce úlohu, aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje a zpřístupnit času procesoru pro jiné úlohy.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-103">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee3d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee3d7-104">Syntax</span></span>  
  
```  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ee3d7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ee3d7-105">Return Value</span></span>  
  
|<span data-ttu-id="ee3d7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee3d7-106">HRESULT</span></span>|<span data-ttu-id="ee3d7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ee3d7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee3d7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee3d7-108">S_OK</span></span>|<span data-ttu-id="ee3d7-109">`YieldTask` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-109">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="ee3d7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ee3d7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ee3d7-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ee3d7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee3d7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ee3d7-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-113">The call timed out.</span></span>|  
|<span data-ttu-id="ee3d7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ee3d7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ee3d7-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ee3d7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ee3d7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ee3d7-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ee3d7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ee3d7-118">E_FAIL</span></span>|<span data-ttu-id="ee3d7-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ee3d7-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ee3d7-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee3d7-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee3d7-122">Remarks</span></span>  
 <span data-ttu-id="ee3d7-123">Hostitel volá `YieldTask` pro požadavky na prostředky procesoru pro jiných úloh nebo procesů.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-123">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="ee3d7-124">Tato metoda je primárně určený umožňující dlouho běžící kód k uvolnění doba využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-124">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="ee3d7-125">Modul runtime pokusí umístit úlohu, aktuální `ICLRTask` instance představují ve stavu, kdy přispět doba zpracování, ale díky žádná záruka úspěch.</span><span class="sxs-lookup"><span data-stu-id="ee3d7-125">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee3d7-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee3d7-126">Requirements</span></span>  
 <span data-ttu-id="ee3d7-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee3d7-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee3d7-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee3d7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee3d7-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee3d7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee3d7-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee3d7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee3d7-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee3d7-131">See Also</span></span>  
 [<span data-ttu-id="ee3d7-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee3d7-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ee3d7-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee3d7-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ee3d7-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee3d7-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ee3d7-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee3d7-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
