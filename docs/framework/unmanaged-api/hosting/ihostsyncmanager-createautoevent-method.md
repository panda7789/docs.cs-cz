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
ms.openlocfilehash: b3778e12dd96d4f4653633252e13469601c4879d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139435"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="511b8-102">IHostSyncManager::CreateAutoEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="511b8-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="511b8-103">Vytvoří objekt události automatického resetování.</span><span class="sxs-lookup"><span data-stu-id="511b8-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="511b8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="511b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="511b8-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="511b8-106">mimo Ukazatel na adresu instance [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) implementované hostitelem nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="511b8-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="511b8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="511b8-107">Return Value</span></span>  
  
|<span data-ttu-id="511b8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="511b8-108">HRESULT</span></span>|<span data-ttu-id="511b8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="511b8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="511b8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="511b8-110">S_OK</span></span>|<span data-ttu-id="511b8-111">`CreateAutoEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="511b8-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="511b8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="511b8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="511b8-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="511b8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="511b8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="511b8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="511b8-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="511b8-115">The call timed out.</span></span>|  
|<span data-ttu-id="511b8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="511b8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="511b8-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="511b8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="511b8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="511b8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="511b8-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="511b8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="511b8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="511b8-120">E_FAIL</span></span>|<span data-ttu-id="511b8-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="511b8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="511b8-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="511b8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="511b8-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="511b8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="511b8-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="511b8-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="511b8-125">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="511b8-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="511b8-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="511b8-126">Remarks</span></span>  
 <span data-ttu-id="511b8-127">`CreateAutoEvent` vytvoří objekt automatické události, jehož stav se automaticky změní na nesignální po uvolnění čekání.</span><span class="sxs-lookup"><span data-stu-id="511b8-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="511b8-128">Tato metoda zrcadlí funkci Win32 `CreateEvent` s hodnotou `false` zadanou pro parametr `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="511b8-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511b8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="511b8-129">Requirements</span></span>  
 <span data-ttu-id="511b8-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="511b8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511b8-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="511b8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="511b8-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="511b8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="511b8-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511b8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511b8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="511b8-134">See also</span></span>

- [<span data-ttu-id="511b8-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="511b8-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="511b8-136">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="511b8-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="511b8-137">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="511b8-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="511b8-138">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="511b8-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
