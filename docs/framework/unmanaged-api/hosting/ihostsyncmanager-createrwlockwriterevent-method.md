---
title: "IHostSyncManager::CreateRWLockWriterEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockWriterEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c89dec681102f96f96f1d7f3e802ded0a2df7b4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="2c1b2-102">IHostSyncManager::CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="2c1b2-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="2c1b2-103">Vytvoří objekt automatickým vynulováním událostí k provádění zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c1b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c1b2-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c1b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c1b2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="2c1b2-106">[v] Soubor cookie přidružit s automatickým vynulováním událostí.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="2c1b2-107">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c1b2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c1b2-108">Return Value</span></span>  
  
|<span data-ttu-id="2c1b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c1b2-109">HRESULT</span></span>|<span data-ttu-id="2c1b2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="2c1b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c1b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c1b2-111">S_OK</span></span>|<span data-ttu-id="2c1b2-112">`CreateRWLockWriterEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="2c1b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c1b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c1b2-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c1b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c1b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c1b2-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="2c1b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c1b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c1b2-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c1b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c1b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c1b2-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c1b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c1b2-121">E_FAIL</span></span>|<span data-ttu-id="2c1b2-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c1b2-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c1b2-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2c1b2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2c1b2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2c1b2-126">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c1b2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c1b2-127">Remarks</span></span>  
 <span data-ttu-id="2c1b2-128">Volání CLR `CreateRWLockWriterEvent` metodu k získání odkazu na `IHostAutoEvent` instance pro použití v jeho implementaci zámek pro zápis.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="2c1b2-129">Hostitele pomocí zadaného souboru cookie můžete určit úkoly, které čekají na zámek voláním metody iterace [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2c1b2-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c1b2-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c1b2-130">Requirements</span></span>  
 <span data-ttu-id="2c1b2-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c1b2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c1b2-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c1b2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c1b2-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c1b2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c1b2-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1b2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1b2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c1b2-135">See Also</span></span>  
 [<span data-ttu-id="2c1b2-136">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c1b2-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="2c1b2-137">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c1b2-137">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="2c1b2-138">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c1b2-138">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="2c1b2-139">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c1b2-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
