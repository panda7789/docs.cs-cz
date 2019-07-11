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
ms.openlocfilehash: 81afc2aa738c719456091c3f28f3ca33682776e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759006"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="93020-102">ICLRTask::ExitTask – metoda</span><span class="sxs-lookup"><span data-stu-id="93020-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="93020-103">Upozorní common language runtime (CLR), která úloha je reprezentována aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance ukončuje a pokusí se řádně úlohu ukončit.</span><span class="sxs-lookup"><span data-stu-id="93020-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93020-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93020-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="93020-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93020-105">Return Value</span></span>  
  
|<span data-ttu-id="93020-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93020-106">HRESULT</span></span>|<span data-ttu-id="93020-107">Popis</span><span class="sxs-lookup"><span data-stu-id="93020-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93020-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="93020-108">S_OK</span></span>|<span data-ttu-id="93020-109">`ExitTask` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="93020-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="93020-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93020-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93020-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="93020-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93020-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93020-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93020-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="93020-113">The call timed out.</span></span>|  
|<span data-ttu-id="93020-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93020-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93020-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="93020-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93020-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93020-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93020-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="93020-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93020-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93020-118">E_FAIL</span></span>|<span data-ttu-id="93020-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="93020-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93020-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="93020-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93020-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="93020-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93020-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93020-122">Remarks</span></span>  
 <span data-ttu-id="93020-123">`ExitTask` pokusy o čistého vypnutí úkolu, způsobem, který je obdobou odpojení vlákna od nespravovaný typ knihovny.</span><span class="sxs-lookup"><span data-stu-id="93020-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93020-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93020-124">Requirements</span></span>  
 <span data-ttu-id="93020-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93020-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93020-126">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93020-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93020-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93020-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93020-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93020-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93020-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93020-129">See also</span></span>

- [<span data-ttu-id="93020-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93020-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="93020-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93020-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="93020-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93020-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="93020-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93020-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
