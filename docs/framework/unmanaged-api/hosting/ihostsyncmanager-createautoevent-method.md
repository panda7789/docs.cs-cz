---
title: IHostSyncManager::CreateAutoEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe1b685f50f793f7451187f17adc848ec9d4422f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440200"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="9a243-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="9a243-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="9a243-103">Vytvoří objekt události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="9a243-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a243-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a243-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a243-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a243-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="9a243-106">[out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci implementované pro hostitele, nebo hodnotu null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="9a243-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a243-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9a243-107">Return Value</span></span>  
  
|<span data-ttu-id="9a243-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a243-108">HRESULT</span></span>|<span data-ttu-id="9a243-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9a243-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a243-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a243-110">S_OK</span></span>|<span data-ttu-id="9a243-111">`CreateAutoEvent` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9a243-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="9a243-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a243-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a243-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9a243-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a243-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a243-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a243-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9a243-115">The call timed out.</span></span>|  
|<span data-ttu-id="9a243-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a243-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a243-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9a243-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a243-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a243-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a243-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9a243-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a243-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a243-120">E_FAIL</span></span>|<span data-ttu-id="9a243-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9a243-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a243-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9a243-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a243-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a243-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a243-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9a243-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9a243-125">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="9a243-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a243-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a243-126">Remarks</span></span>  
 <span data-ttu-id="9a243-127">`CreateAutoEvent` Vytvoří objekt automatické událostí, jejichž stav se automaticky změní na jiný signál po vydala čekání na vlákno.</span><span class="sxs-lookup"><span data-stu-id="9a243-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="9a243-128">Tato metoda odpovídá Win32 `CreateEvent` funkce s hodnotou `false` zadaná pro `bManualReset` parametr</span><span class="sxs-lookup"><span data-stu-id="9a243-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a243-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a243-129">Requirements</span></span>  
 <span data-ttu-id="9a243-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a243-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a243-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a243-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a243-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a243-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a243-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a243-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a243-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a243-134">See Also</span></span>  
 [<span data-ttu-id="9a243-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a243-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9a243-136">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a243-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9a243-137">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a243-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="9a243-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a243-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
