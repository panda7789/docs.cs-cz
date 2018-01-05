---
title: "IHostCrst::Leave – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.Leave
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 391aff3920e7ea2ef010ce7d97bdedb4e636dc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="c0dee-102">IHostCrst::Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="c0dee-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="c0dee-103">Ponechá kritické části, která je reprezentována aktuální instancí třídy [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c0dee-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0dee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0dee-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c0dee-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c0dee-105">Return Value</span></span>  
  
|<span data-ttu-id="c0dee-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0dee-106">HRESULT</span></span>|<span data-ttu-id="c0dee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c0dee-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0dee-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0dee-108">S_OK</span></span>|<span data-ttu-id="c0dee-109">`Leave`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c0dee-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="c0dee-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c0dee-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c0dee-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c0dee-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c0dee-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c0dee-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c0dee-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c0dee-113">The call timed out.</span></span>|  
|<span data-ttu-id="c0dee-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c0dee-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c0dee-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="c0dee-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c0dee-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c0dee-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c0dee-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="c0dee-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c0dee-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c0dee-118">E_FAIL</span></span>|<span data-ttu-id="c0dee-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="c0dee-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c0dee-120">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c0dee-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c0dee-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c0dee-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0dee-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0dee-122">Remarks</span></span>  
 <span data-ttu-id="c0dee-123">`Leave`Umožňuje CLR komunikovat přímo s hostitele dělení na vlákna implementace, nikoli pomocí odpovídající Win32 `LeaveCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="c0dee-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="c0dee-124">Vlákno, která přebírá vlastnictví kritická sekce reprezentována aktuální `IHostCrst` instance musí volat `Leave` po pokaždé, když se zadá tuto část, kritické.</span><span class="sxs-lookup"><span data-stu-id="c0dee-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0dee-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0dee-125">Requirements</span></span>  
 <span data-ttu-id="c0dee-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0dee-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0dee-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c0dee-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0dee-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0dee-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0dee-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0dee-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0dee-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0dee-130">See Also</span></span>  
 [<span data-ttu-id="c0dee-131">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0dee-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c0dee-132">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0dee-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="c0dee-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c0dee-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
