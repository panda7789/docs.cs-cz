---
title: ICLRTask::Abort – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46d60ff6ab64d57ca5c7020877758657b61125ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434834"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="9800b-102">ICLRTask::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="9800b-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="9800b-103">Požadavky, modul CLR (CLR) přerušit úlohu, aktuální [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance představuje.</span><span class="sxs-lookup"><span data-stu-id="9800b-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9800b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9800b-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9800b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9800b-105">Return Value</span></span>  
  
|<span data-ttu-id="9800b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9800b-106">HRESULT</span></span>|<span data-ttu-id="9800b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9800b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9800b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9800b-108">S_OK</span></span>|<span data-ttu-id="9800b-109">`Abort` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9800b-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="9800b-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9800b-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9800b-111">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9800b-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9800b-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9800b-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9800b-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9800b-113">The call timed out.</span></span>|  
|<span data-ttu-id="9800b-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9800b-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9800b-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9800b-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9800b-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9800b-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9800b-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9800b-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9800b-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9800b-118">E_FAIL</span></span>|<span data-ttu-id="9800b-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9800b-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9800b-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9800b-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9800b-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9800b-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9800b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9800b-122">Remarks</span></span>  
 <span data-ttu-id="9800b-123">Vyvolá modulu CLR <xref:System.Threading.ThreadAbortException> při volání hostitele `Abort`.</span><span class="sxs-lookup"><span data-stu-id="9800b-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="9800b-124">Vrátí hned po inicializaci informace o výjimce, bez čekání na uživatelského kódu, například finalizační metody nebo zpracování mechanismů výjimek provést.</span><span class="sxs-lookup"><span data-stu-id="9800b-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="9800b-125">Volání `Abort` proto rychle vrátit.</span><span class="sxs-lookup"><span data-stu-id="9800b-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9800b-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9800b-126">Requirements</span></span>  
 <span data-ttu-id="9800b-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9800b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9800b-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9800b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9800b-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9800b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9800b-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9800b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9800b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9800b-131">See Also</span></span>  
 [<span data-ttu-id="9800b-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9800b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="9800b-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9800b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="9800b-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9800b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="9800b-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9800b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
