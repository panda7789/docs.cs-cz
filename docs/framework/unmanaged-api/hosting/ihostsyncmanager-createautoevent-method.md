---
title: "IHostSyncManager::CreateAutoEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6a792ca9075e48a8092d92e1adf870174dd1af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="93571-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="93571-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="93571-103">Vytvoří objekt události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="93571-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93571-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93571-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93571-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93571-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="93571-106">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci implementované pro hostitele, nebo hodnotu null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="93571-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93571-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93571-107">Return Value</span></span>  
  
|<span data-ttu-id="93571-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93571-108">HRESULT</span></span>|<span data-ttu-id="93571-109">Popis</span><span class="sxs-lookup"><span data-stu-id="93571-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93571-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93571-110">S_OK</span></span>|<span data-ttu-id="93571-111">`CreateAutoEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="93571-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="93571-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93571-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93571-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="93571-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93571-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93571-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93571-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="93571-115">The call timed out.</span></span>|  
|<span data-ttu-id="93571-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93571-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93571-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="93571-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93571-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93571-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93571-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="93571-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93571-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93571-120">E_FAIL</span></span>|<span data-ttu-id="93571-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="93571-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93571-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="93571-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93571-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="93571-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="93571-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="93571-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="93571-125">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="93571-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93571-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93571-126">Remarks</span></span>  
 <span data-ttu-id="93571-127">`CreateAutoEvent`Vytvoří objekt automatické událostí, jejichž stav se automaticky změní na jiný signál po vydala čekání na vlákno.</span><span class="sxs-lookup"><span data-stu-id="93571-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="93571-128">Tato metoda odpovídá Win32 `CreateEvent` funkce s hodnotou `false` zadaná pro `bManualReset` parametr</span><span class="sxs-lookup"><span data-stu-id="93571-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93571-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93571-129">Requirements</span></span>  
 <span data-ttu-id="93571-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93571-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93571-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93571-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93571-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93571-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93571-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93571-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93571-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="93571-134">See Also</span></span>  
 [<span data-ttu-id="93571-135">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93571-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="93571-136">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93571-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="93571-137">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93571-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="93571-138">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93571-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
