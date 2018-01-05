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
ms.workload: dotnet
ms.openlocfilehash: d1bbd10437662fc8b7fbb52d65d196d7a519538b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="44607-102">IHostManualEvent::Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="44607-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="44607-103">Obnoví aktuální [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance do stavu signál.</span><span class="sxs-lookup"><span data-stu-id="44607-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44607-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44607-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="44607-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="44607-105">Return Value</span></span>  
  
|<span data-ttu-id="44607-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44607-106">HRESULT</span></span>|<span data-ttu-id="44607-107">Popis</span><span class="sxs-lookup"><span data-stu-id="44607-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44607-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="44607-108">S_OK</span></span>|<span data-ttu-id="44607-109">`Reset`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="44607-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="44607-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44607-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44607-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="44607-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44607-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44607-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44607-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="44607-113">The call timed out.</span></span>|  
|<span data-ttu-id="44607-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44607-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44607-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="44607-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44607-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44607-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44607-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="44607-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44607-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44607-118">E_FAIL</span></span>|<span data-ttu-id="44607-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="44607-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44607-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="44607-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44607-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44607-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44607-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44607-122">Requirements</span></span>  
 <span data-ttu-id="44607-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44607-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44607-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44607-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44607-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44607-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44607-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44607-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44607-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="44607-127">See Also</span></span>  
 [<span data-ttu-id="44607-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44607-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="44607-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44607-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="44607-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44607-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="44607-131">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44607-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="44607-132">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44607-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
