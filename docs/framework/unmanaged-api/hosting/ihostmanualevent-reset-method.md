---
title: IHostManualEvent::Reset – metoda
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e19b64e5de4058bd63a425090a09c5ec7984faf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556308"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="38d86-102">IHostManualEvent::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="38d86-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="38d86-103">Obnoví aktuální [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance do nesignálového stavu.</span><span class="sxs-lookup"><span data-stu-id="38d86-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38d86-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="38d86-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38d86-105">Return Value</span></span>  
  
|<span data-ttu-id="38d86-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38d86-106">HRESULT</span></span>|<span data-ttu-id="38d86-107">Popis</span><span class="sxs-lookup"><span data-stu-id="38d86-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38d86-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="38d86-108">S_OK</span></span>|<span data-ttu-id="38d86-109">`Reset` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="38d86-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="38d86-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38d86-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38d86-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="38d86-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38d86-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38d86-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38d86-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="38d86-113">The call timed out.</span></span>|  
|<span data-ttu-id="38d86-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38d86-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38d86-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="38d86-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38d86-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38d86-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38d86-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="38d86-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38d86-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38d86-118">E_FAIL</span></span>|<span data-ttu-id="38d86-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="38d86-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38d86-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="38d86-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38d86-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="38d86-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38d86-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38d86-122">Requirements</span></span>  
 <span data-ttu-id="38d86-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38d86-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d86-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="38d86-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38d86-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38d86-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38d86-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d86-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d86-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38d86-127">See also</span></span>
- [<span data-ttu-id="38d86-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38d86-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="38d86-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38d86-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="38d86-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38d86-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="38d86-131">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38d86-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="38d86-132">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38d86-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
