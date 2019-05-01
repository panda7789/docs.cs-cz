---
title: IHostManualEvent::Set – metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 674745636033f42eb8fb67babf6f5a3f013491c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993210"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="8d341-102">IHostManualEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="8d341-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="8d341-103">Nastaví aktuální [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="8d341-103">Sets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d341-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8d341-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d341-105">Return Value</span></span>  
  
|<span data-ttu-id="8d341-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d341-106">HRESULT</span></span>|<span data-ttu-id="8d341-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8d341-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d341-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d341-108">S_OK</span></span>|<span data-ttu-id="8d341-109">`Set` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8d341-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="8d341-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d341-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d341-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d341-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d341-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d341-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d341-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d341-113">The call timed out.</span></span>|  
|<span data-ttu-id="8d341-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d341-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d341-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8d341-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d341-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d341-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d341-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8d341-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d341-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d341-118">E_FAIL</span></span>|<span data-ttu-id="8d341-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8d341-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d341-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8d341-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d341-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d341-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d341-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d341-122">Requirements</span></span>  
 <span data-ttu-id="8d341-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d341-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d341-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d341-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d341-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d341-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d341-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d341-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d341-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d341-127">See also</span></span>

- [<span data-ttu-id="8d341-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d341-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="8d341-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d341-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="8d341-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d341-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="8d341-131">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d341-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="8d341-132">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d341-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
