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
ms.openlocfilehash: b7994757a127686967d9863a574d0e1f8425ca86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521215"
---
# <a name="ihostautoeventset-method"></a><span data-ttu-id="c61a7-102">IHostAutoEvent::Set – metoda</span><span class="sxs-lookup"><span data-stu-id="c61a7-102">IHostAutoEvent::Set Method</span></span>
<span data-ttu-id="c61a7-103">Nastaví aktuální [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="c61a7-103">Sets the current [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c61a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c61a7-104">Syntax</span></span>  
  
```  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c61a7-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c61a7-105">Return Value</span></span>  
  
|<span data-ttu-id="c61a7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c61a7-106">HRESULT</span></span>|<span data-ttu-id="c61a7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c61a7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c61a7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c61a7-108">S_OK</span></span>|<span data-ttu-id="c61a7-109">`Set` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c61a7-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="c61a7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c61a7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c61a7-111">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c61a7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c61a7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c61a7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c61a7-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c61a7-113">The call timed out.</span></span>|  
|<span data-ttu-id="c61a7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c61a7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c61a7-115">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c61a7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c61a7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c61a7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c61a7-117">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c61a7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c61a7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c61a7-118">E_FAIL</span></span>|<span data-ttu-id="c61a7-119">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c61a7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c61a7-120">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c61a7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c61a7-121">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c61a7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c61a7-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c61a7-122">Requirements</span></span>  
 <span data-ttu-id="c61a7-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c61a7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c61a7-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c61a7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c61a7-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c61a7-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c61a7-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c61a7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61a7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c61a7-127">See also</span></span>
- [<span data-ttu-id="c61a7-128">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c61a7-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c61a7-129">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c61a7-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="c61a7-130">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c61a7-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="c61a7-131">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c61a7-131">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
