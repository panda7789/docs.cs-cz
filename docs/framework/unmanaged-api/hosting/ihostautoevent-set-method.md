---
title: IHostAutoEvent::Set – metoda
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Set
helpviewer_keywords:
- Set method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Set method [.NET Framework hosting]
ms.assetid: 46becf3e-bc0e-4338-85c0-9ab0df76a1d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af9f55bdcfe23f0b2a051b33cb1280f312820a7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227012"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="e71a9-102">IHostAutoEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="e71a9-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="e71a9-103">Nastaví aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="e71a9-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e71a9-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e71a9-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e71a9-105">Return Value</span></span>  
  
|<span data-ttu-id="e71a9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e71a9-106">HRESULT</span></span>|<span data-ttu-id="e71a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e71a9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e71a9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e71a9-108">S_OK</span></span>|`Set` <span data-ttu-id="e71a9-109">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e71a9-109">returned successfully.</span></span>|  
|<span data-ttu-id="e71a9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e71a9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e71a9-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e71a9-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e71a9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e71a9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e71a9-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e71a9-113">The call timed out.</span></span>|  
|<span data-ttu-id="e71a9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e71a9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e71a9-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="e71a9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e71a9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e71a9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e71a9-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="e71a9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e71a9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e71a9-118">E_FAIL</span></span>|<span data-ttu-id="e71a9-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="e71a9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e71a9-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e71a9-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e71a9-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e71a9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e71a9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e71a9-122">Requirements</span></span>  
 <span data-ttu-id="e71a9-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e71a9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e71a9-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e71a9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e71a9-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e71a9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e71a9-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e71a9-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e71a9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e71a9-127">See also</span></span>

- [<span data-ttu-id="e71a9-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e71a9-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e71a9-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e71a9-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="e71a9-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e71a9-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e71a9-131">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e71a9-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
