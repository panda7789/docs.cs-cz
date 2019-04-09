---
title: IHostTaskManager::EndDelayAbort – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d12e5cab41f016ddee78089dc1df1f5c942ecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194443"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="0495e-102">IHostTaskManager::EndDelayAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="0495e-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="0495e-103">Upozorní na hostitele, spravovaný kód se ukončuje období, ve kterém nesmí být aktuální úloha přerušena, po dřívějším volání [ihosttaskmanager::begindelayabort –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="0495e-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0495e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0495e-104">Syntax</span></span>  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0495e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0495e-105">Return Value</span></span>  
  
|<span data-ttu-id="0495e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0495e-106">HRESULT</span></span>|<span data-ttu-id="0495e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0495e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0495e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0495e-108">S_OK</span></span>|`EndDelayAbort` <span data-ttu-id="0495e-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0495e-109">returned successfully.</span></span>|  
|<span data-ttu-id="0495e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0495e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0495e-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0495e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0495e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0495e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0495e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0495e-113">The call timed out.</span></span>|  
|<span data-ttu-id="0495e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0495e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0495e-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="0495e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0495e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0495e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0495e-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="0495e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0495e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0495e-118">E_FAIL</span></span>|<span data-ttu-id="0495e-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="0495e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0495e-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0495e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0495e-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0495e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0495e-122">E_UNEXPECTED, JE-</span><span class="sxs-lookup"><span data-stu-id="0495e-122">E_UNEXPECTED</span></span>|`EndDelayAbort` <span data-ttu-id="0495e-123">byla volána bez odpovídajícího volání `BeginDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="0495e-123">was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0495e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0495e-124">Remarks</span></span>  
 <span data-ttu-id="0495e-125">Modul CLR provede odpovídající volání `BeginDelayAbort` v aktuální úloze před voláním `EndDelayAbort`.</span><span class="sxs-lookup"><span data-stu-id="0495e-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="0495e-126">Chybí odpovídající volání provádění hostitele [ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) by měla vrátit e_unexpected, je-z `EndDelayAbort`a neměla by mít žádné akce.</span><span class="sxs-lookup"><span data-stu-id="0495e-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0495e-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0495e-127">Requirements</span></span>  
 <span data-ttu-id="0495e-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0495e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0495e-129">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0495e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0495e-130">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0495e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0495e-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0495e-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0495e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0495e-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="0495e-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0495e-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0495e-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0495e-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0495e-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0495e-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0495e-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0495e-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
