---
title: "IHostSyncManager::CreateRWLockWriterEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eb38cd76a051b1a4459dff4f8164a6405f5fb32d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="d2d66-102">IHostSyncManager::CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="d2d66-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="d2d66-103">Vytvoří objekt automatickým vynulováním událostí k provádění zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="d2d66-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2d66-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2d66-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2d66-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="d2d66-106">[v] Soubor cookie přidružit s automatickým vynulováním událostí.</span><span class="sxs-lookup"><span data-stu-id="d2d66-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="d2d66-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="d2d66-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2d66-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2d66-108">Return Value</span></span>  
  
|<span data-ttu-id="d2d66-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2d66-109">HRESULT</span></span>|<span data-ttu-id="d2d66-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d2d66-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2d66-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2d66-111">S_OK</span></span>|<span data-ttu-id="d2d66-112">`CreateRWLockWriterEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d2d66-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="d2d66-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2d66-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2d66-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d2d66-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2d66-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2d66-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2d66-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d2d66-116">The call timed out.</span></span>|  
|<span data-ttu-id="d2d66-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2d66-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2d66-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d2d66-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2d66-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2d66-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2d66-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d2d66-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2d66-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2d66-121">E_FAIL</span></span>|<span data-ttu-id="d2d66-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d2d66-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2d66-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d2d66-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2d66-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2d66-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d2d66-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d2d66-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d2d66-126">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="d2d66-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2d66-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2d66-127">Remarks</span></span>  
 <span data-ttu-id="d2d66-128">Volání CLR `CreateRWLockWriterEvent` metodu k získání odkazu na `IHostAutoEvent` instance pro použití v jeho implementaci zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="d2d66-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="d2d66-129">Hostitele pomocí zadaného souboru cookie můžete určit úkoly, které čekají na zámek voláním metody iterace [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2d66-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d66-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2d66-130">Requirements</span></span>  
 <span data-ttu-id="d2d66-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d66-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d66-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2d66-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2d66-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2d66-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2d66-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2d66-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d66-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2d66-135">See Also</span></span>  
 [<span data-ttu-id="d2d66-136">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d66-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d2d66-137">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d66-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="d2d66-138">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d66-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="d2d66-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d66-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
