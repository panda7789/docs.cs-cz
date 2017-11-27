---
title: "IHostManualEvent::Reset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e41922cb1732fe4e6727408692bbc7b99288e6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="1e20e-102">IHostManualEvent::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="1e20e-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="1e20e-103">Obnoví aktuální [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance do stavu signál.</span><span class="sxs-lookup"><span data-stu-id="1e20e-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e20e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e20e-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1e20e-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1e20e-105">Return Value</span></span>  
  
|<span data-ttu-id="1e20e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e20e-106">HRESULT</span></span>|<span data-ttu-id="1e20e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1e20e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e20e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e20e-108">S_OK</span></span>|<span data-ttu-id="1e20e-109">`Reset`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1e20e-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="1e20e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e20e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e20e-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1e20e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e20e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e20e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e20e-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1e20e-113">The call timed out.</span></span>|  
|<span data-ttu-id="1e20e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e20e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e20e-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="1e20e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e20e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e20e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e20e-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="1e20e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e20e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e20e-118">E_FAIL</span></span>|<span data-ttu-id="1e20e-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="1e20e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e20e-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1e20e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e20e-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1e20e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e20e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e20e-122">Requirements</span></span>  
 <span data-ttu-id="1e20e-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e20e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e20e-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e20e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e20e-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e20e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e20e-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e20e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e20e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e20e-127">See Also</span></span>  
 [<span data-ttu-id="1e20e-128">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e20e-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1e20e-129">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e20e-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="1e20e-130">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e20e-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="1e20e-131">Ihostsemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e20e-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="1e20e-132">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e20e-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
