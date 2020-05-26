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
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803325"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="8935f-102">IHostSyncManager::CreateMonitorEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="8935f-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="8935f-103">Vytvoří monitorovaný objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="8935f-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8935f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8935f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8935f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8935f-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8935f-106">pro Soubor cookie, který se má přidružit k objektu události.</span><span class="sxs-lookup"><span data-stu-id="8935f-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8935f-107">mimo Ukazatel na adresu instance [IHostAutoEvent](ihostautoevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8935f-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8935f-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8935f-108">Return Value</span></span>  
  
|<span data-ttu-id="8935f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8935f-109">HRESULT</span></span>|<span data-ttu-id="8935f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8935f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8935f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8935f-111">S_OK</span></span>|<span data-ttu-id="8935f-112">`CreateMonitorEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8935f-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8935f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8935f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8935f-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8935f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8935f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8935f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8935f-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8935f-116">The call timed out.</span></span>|  
|<span data-ttu-id="8935f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8935f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8935f-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8935f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8935f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8935f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8935f-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8935f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8935f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8935f-121">E_FAIL</span></span>|<span data-ttu-id="8935f-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8935f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8935f-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8935f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8935f-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8935f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8935f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8935f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8935f-126">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8935f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8935f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8935f-127">Remarks</span></span>  
 <span data-ttu-id="8935f-128">`CreateMonitorEvent`Vrátí `IHostAutoEvent` , že CLR používá při implementaci spravovaného <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="8935f-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="8935f-129">Tato metoda zrcadlí `CreateEvent` funkci Win32 s hodnotou `false` zadanou pro `bManualReset` parametr.</span><span class="sxs-lookup"><span data-stu-id="8935f-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="8935f-130">Hostitel může pomocí souboru cookie určit, který úkol čeká na monitorování voláním metody [ICLRSyncManager:: GetMonitorOwner –](iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8935f-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8935f-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8935f-131">Requirements</span></span>  
 <span data-ttu-id="8935f-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8935f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8935f-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8935f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8935f-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8935f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8935f-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8935f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8935f-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="8935f-136">See also</span></span>

- [<span data-ttu-id="8935f-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8935f-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8935f-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8935f-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8935f-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8935f-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
