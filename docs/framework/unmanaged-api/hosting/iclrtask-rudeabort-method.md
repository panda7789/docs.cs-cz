---
title: ICLRTask::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2db47f90e73922858013885e99e953ddcacbd450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763513"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="d518b-102">ICLRTask::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="d518b-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="d518b-103">Dává pokyn common language runtime (CLR) na zrušení úlohy reprezentované aktuální [iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance okamžitě a nepodmíněně.</span><span class="sxs-lookup"><span data-stu-id="d518b-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d518b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d518b-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="d518b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d518b-105">Return Value</span></span>  
  
|<span data-ttu-id="d518b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d518b-106">HRESULT</span></span>|<span data-ttu-id="d518b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d518b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d518b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d518b-108">S_OK</span></span>|<span data-ttu-id="d518b-109">`RudeAbort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d518b-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="d518b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d518b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d518b-111">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d518b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d518b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d518b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d518b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d518b-113">The call timed out.</span></span>|  
|<span data-ttu-id="d518b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d518b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d518b-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d518b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d518b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d518b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d518b-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d518b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d518b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d518b-118">E_FAIL</span></span>|<span data-ttu-id="d518b-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d518b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d518b-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d518b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d518b-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d518b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d518b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d518b-122">Remarks</span></span>  
 <span data-ttu-id="d518b-123">Volá hostitele `RudeAbort` přerušit úlohu okamžitě.</span><span class="sxs-lookup"><span data-stu-id="d518b-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="d518b-124">Finalizační metody a rutiny zpracování výjimek není zaručeno, že má být proveden.</span><span class="sxs-lookup"><span data-stu-id="d518b-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d518b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d518b-125">Requirements</span></span>  
 <span data-ttu-id="d518b-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d518b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d518b-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d518b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d518b-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d518b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d518b-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d518b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d518b-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d518b-130">See also</span></span>

- [<span data-ttu-id="d518b-131">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d518b-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d518b-132">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d518b-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d518b-133">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d518b-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d518b-134">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d518b-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
