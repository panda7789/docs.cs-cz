---
title: IHostSyncManager::CreateMonitorEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192021"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="60310-102">IHostSyncManager::CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="60310-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="60310-103">Vytvoří monitorovaný objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="60310-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60310-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60310-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60310-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60310-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="60310-106">pro Soubor cookie, který se má přidružit k objektu události.</span><span class="sxs-lookup"><span data-stu-id="60310-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="60310-107">mimo Ukazatel na adresu instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="60310-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60310-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60310-108">Return Value</span></span>  
  
|<span data-ttu-id="60310-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60310-109">HRESULT</span></span>|<span data-ttu-id="60310-110">Popis</span><span class="sxs-lookup"><span data-stu-id="60310-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60310-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="60310-111">S_OK</span></span>|<span data-ttu-id="60310-112">`CreateMonitorEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="60310-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="60310-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60310-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60310-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="60310-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60310-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60310-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60310-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="60310-116">The call timed out.</span></span>|  
|<span data-ttu-id="60310-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60310-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60310-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="60310-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60310-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60310-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60310-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="60310-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60310-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60310-121">E_FAIL</span></span>|<span data-ttu-id="60310-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="60310-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60310-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="60310-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60310-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60310-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="60310-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="60310-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="60310-126">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="60310-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60310-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60310-127">Remarks</span></span>  
 <span data-ttu-id="60310-128">`CreateMonitorEvent` vrátí `IHostAutoEvent`, který CLR používá při implementaci spravovaného typu <xref:System.Threading.Monitor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="60310-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="60310-129">Tato metoda zrcadlí funkci Win32 `CreateEvent` s hodnotou `false` zadanou pro parametr `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="60310-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="60310-130">Hostitel může pomocí souboru cookie určit, který úkol čeká na monitorování voláním metody [ICLRSyncManager:: GetMonitorOwner –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="60310-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60310-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60310-131">Requirements</span></span>  
 <span data-ttu-id="60310-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60310-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60310-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60310-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60310-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60310-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60310-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60310-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60310-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60310-136">See also</span></span>

- [<span data-ttu-id="60310-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60310-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="60310-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60310-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="60310-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60310-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
