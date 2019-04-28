---
title: ICLRTask::ExitTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a55b62c7c71510435b980a4e5938c20628046f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763624"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="5b231-102">ICLRTask::ExitTask – metoda</span><span class="sxs-lookup"><span data-stu-id="5b231-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="5b231-103">Upozorní common language runtime (CLR), která úloha je reprezentována aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance ukončuje a pokusí se řádně úlohu ukončit.</span><span class="sxs-lookup"><span data-stu-id="5b231-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b231-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b231-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5b231-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b231-105">Return Value</span></span>  
  
|<span data-ttu-id="5b231-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b231-106">HRESULT</span></span>|<span data-ttu-id="5b231-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5b231-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b231-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b231-108">S_OK</span></span>|<span data-ttu-id="5b231-109">`ExitTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5b231-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="5b231-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b231-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b231-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5b231-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b231-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b231-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b231-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5b231-113">The call timed out.</span></span>|  
|<span data-ttu-id="5b231-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b231-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b231-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="5b231-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b231-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b231-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b231-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="5b231-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b231-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b231-118">E_FAIL</span></span>|<span data-ttu-id="5b231-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="5b231-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b231-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="5b231-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b231-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b231-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b231-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b231-122">Remarks</span></span>  
 <span data-ttu-id="5b231-123">`ExitTask` pokusy o čistého vypnutí úkolu, způsobem, který je obdobou odpojení vlákna od nespravovaný typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="5b231-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b231-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b231-124">Requirements</span></span>  
 <span data-ttu-id="5b231-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b231-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b231-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b231-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b231-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b231-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b231-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b231-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b231-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b231-129">See also</span></span>

- [<span data-ttu-id="5b231-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b231-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5b231-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b231-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5b231-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b231-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5b231-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b231-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
