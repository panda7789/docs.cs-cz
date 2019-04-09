---
title: IHostCrst::Leave – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d60cdee0a5357f7e117dc902b073049f3bbaea9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198475"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="7ee0d-102">IHostCrst::Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="7ee0d-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="7ee0d-103">Ponechá kritický oddíl, která je reprezentována aktuální instancí třídy [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7ee0d-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ee0d-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7ee0d-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7ee0d-105">Return Value</span></span>  
  
|<span data-ttu-id="7ee0d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ee0d-106">HRESULT</span></span>|<span data-ttu-id="7ee0d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7ee0d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ee0d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ee0d-108">S_OK</span></span>|`Leave` <span data-ttu-id="7ee0d-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-109">returned successfully.</span></span>|  
|<span data-ttu-id="7ee0d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ee0d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ee0d-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ee0d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7ee0d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7ee0d-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-113">The call timed out.</span></span>|  
|<span data-ttu-id="7ee0d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7ee0d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7ee0d-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7ee0d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7ee0d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7ee0d-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7ee0d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ee0d-118">E_FAIL</span></span>|<span data-ttu-id="7ee0d-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ee0d-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ee0d-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ee0d-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ee0d-122">Remarks</span></span>  
 `Leave` <span data-ttu-id="7ee0d-123">Umožňuje CLR k přímé komunikaci s hostitele dělení na vlákna provádění, spíš než odpovídající Win32 `LeaveCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-123">allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="7ee0d-124">Vlákno, které převezme vlastnictví kritický oddíl reprezentované aktuální `IHostCrst` musí volat instanci `Leave` po pokaždé, když se zadá tento kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="7ee0d-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee0d-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ee0d-125">Requirements</span></span>  
 <span data-ttu-id="7ee0d-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee0d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee0d-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ee0d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ee0d-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ee0d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7ee0d-129">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7ee0d-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ee0d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ee0d-130">See also</span></span>

- [<span data-ttu-id="7ee0d-131">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ee0d-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7ee0d-132">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ee0d-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="7ee0d-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ee0d-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
