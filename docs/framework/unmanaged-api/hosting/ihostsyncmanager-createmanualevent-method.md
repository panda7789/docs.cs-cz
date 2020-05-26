---
title: IHostSyncManager::CreateManualEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 334520df749ba428e6480188cd0655bb734725a6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803308"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="15eff-102">IHostSyncManager::CreateManualEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="15eff-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="15eff-103">Vytvoří objekt události ručního resetování.</span><span class="sxs-lookup"><span data-stu-id="15eff-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15eff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15eff-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15eff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15eff-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="15eff-106">[in] `true` , pokud je objekt signalizována. v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="15eff-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="15eff-107">mimo Ukazatel na adresu instance [IHostManualEvent](ihostmanualevent-interface.md) nebo hodnotu null, pokud událost nemohla být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="15eff-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15eff-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="15eff-108">Return Value</span></span>  
  
|<span data-ttu-id="15eff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15eff-109">HRESULT</span></span>|<span data-ttu-id="15eff-110">Popis</span><span class="sxs-lookup"><span data-stu-id="15eff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15eff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="15eff-111">S_OK</span></span>|<span data-ttu-id="15eff-112">`CreateManualEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="15eff-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="15eff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15eff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15eff-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="15eff-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15eff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15eff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15eff-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="15eff-116">The call timed out.</span></span>|  
|<span data-ttu-id="15eff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15eff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15eff-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="15eff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15eff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15eff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15eff-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="15eff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15eff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15eff-121">E_FAIL</span></span>|<span data-ttu-id="15eff-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="15eff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15eff-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="15eff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15eff-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="15eff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="15eff-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="15eff-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="15eff-126">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="15eff-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15eff-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15eff-127">Remarks</span></span>  
 <span data-ttu-id="15eff-128">`CreateManualEvent`vytvoří `IHostManualEvent` objekt události ručního resetování, který vyžaduje volání metody [IHostManualEvent:: Reset](ihostmanualevent-reset-method.md) pro nastavení na nesignálný stav.</span><span class="sxs-lookup"><span data-stu-id="15eff-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="15eff-129">`CreateManualEvent`zrcadlí `CreateEvent` funkci Win32 s hodnotou `true` zadanou pro `bManualReset` parametr.</span><span class="sxs-lookup"><span data-stu-id="15eff-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15eff-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15eff-130">Requirements</span></span>  
 <span data-ttu-id="15eff-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15eff-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15eff-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15eff-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15eff-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15eff-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15eff-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15eff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15eff-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="15eff-135">See also</span></span>

- [<span data-ttu-id="15eff-136">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15eff-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="15eff-137">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15eff-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="15eff-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15eff-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
