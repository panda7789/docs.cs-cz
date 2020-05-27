---
title: IHostSyncManager::CreateRWLockWriterEvent – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: f00d166541f7955516e9d5c1dce2a4342c08ad0a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803150"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="8f1b2-102">IHostSyncManager::CreateRWLockWriterEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="8f1b2-102">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>
<span data-ttu-id="8f1b2-103">Vytvoří objekt události automatického resetování pro implementaci zámku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-103">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f1b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f1b2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f1b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f1b2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8f1b2-106">pro Soubor cookie, který se má přidružit k události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-106">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8f1b2-107">mimo Ukazatel na adresu instance [IHostAutoEvent](ihostautoevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f1b2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8f1b2-108">Return Value</span></span>  
  
|<span data-ttu-id="8f1b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f1b2-109">HRESULT</span></span>|<span data-ttu-id="8f1b2-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8f1b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f1b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f1b2-111">S_OK</span></span>|<span data-ttu-id="8f1b2-112">`CreateRWLockWriterEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-112">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8f1b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f1b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f1b2-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f1b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f1b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f1b2-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="8f1b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f1b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f1b2-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f1b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f1b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f1b2-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f1b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f1b2-121">E_FAIL</span></span>|<span data-ttu-id="8f1b2-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f1b2-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f1b2-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f1b2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8f1b2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8f1b2-126">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f1b2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f1b2-127">Remarks</span></span>  
 <span data-ttu-id="8f1b2-128">Modul CLR volá `CreateRWLockWriterEvent` metodu, aby získal odkaz na `IHostAutoEvent` instanci, která se má použít při implementaci zámku zapisovače.</span><span class="sxs-lookup"><span data-stu-id="8f1b2-128">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="8f1b2-129">Hostitel může pomocí zadaného souboru cookie určit, které úlohy čekají na zámek voláním metod iterace rozhraní [ICLRSyncManager](iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8f1b2-129">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f1b2-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f1b2-130">Requirements</span></span>  
 <span data-ttu-id="8f1b2-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f1b2-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f1b2-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8f1b2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f1b2-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8f1b2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f1b2-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f1b2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f1b2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f1b2-135">See also</span></span>

- [<span data-ttu-id="8f1b2-136">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f1b2-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8f1b2-137">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f1b2-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8f1b2-138">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f1b2-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8f1b2-139">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f1b2-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
