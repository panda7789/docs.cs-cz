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
ms.openlocfilehash: ba221beaa0edce49e75f75edddaee72e1beb9747
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803505"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="6c55e-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="6c55e-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="6c55e-103">Vytvoří objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="6c55e-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c55e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c55e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c55e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c55e-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="6c55e-106">mimo Ukazatel na adresu instance [IHostAutoEvent](ihostautoevent-interface.md) implementované hostitelem nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="6c55e-106">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c55e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c55e-107">Return Value</span></span>  
  
|<span data-ttu-id="6c55e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c55e-108">HRESULT</span></span>|<span data-ttu-id="6c55e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6c55e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c55e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c55e-110">S_OK</span></span>|<span data-ttu-id="6c55e-111">`CreateAutoEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6c55e-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="6c55e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c55e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c55e-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6c55e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c55e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c55e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c55e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6c55e-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c55e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c55e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c55e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="6c55e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c55e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c55e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c55e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="6c55e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c55e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c55e-120">E_FAIL</span></span>|<span data-ttu-id="6c55e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="6c55e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c55e-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="6c55e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c55e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c55e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c55e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6c55e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6c55e-125">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6c55e-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c55e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c55e-126">Remarks</span></span>  
 <span data-ttu-id="6c55e-127">`CreateAutoEvent`Vytvoří objekt automatické události, jehož stav je automaticky změněn na nesignální po uvolnění vlákna čekání.</span><span class="sxs-lookup"><span data-stu-id="6c55e-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="6c55e-128">Tato metoda zrcadlí `CreateEvent` funkci Win32 s hodnotou `false` zadanou pro `bManualReset` parametr.</span><span class="sxs-lookup"><span data-stu-id="6c55e-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c55e-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c55e-129">Requirements</span></span>  
 <span data-ttu-id="6c55e-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c55e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c55e-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6c55e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c55e-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6c55e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c55e-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c55e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c55e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c55e-134">See also</span></span>

- [<span data-ttu-id="6c55e-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c55e-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6c55e-136">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c55e-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="6c55e-137">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c55e-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="6c55e-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c55e-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
