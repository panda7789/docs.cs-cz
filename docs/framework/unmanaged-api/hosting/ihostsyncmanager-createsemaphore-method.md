---
title: IHostSyncManager::CreateSemaphore – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 680280e959d523356b95a5a4d9390c80720c0330
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803141"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="26640-102">IHostSyncManager::CreateSemaphore – metoda</span><span class="sxs-lookup"><span data-stu-id="26640-102">IHostSyncManager::CreateSemaphore Method</span></span>
<span data-ttu-id="26640-103">Vytvoří objekt [IHostSemaphore](ihostsemaphore-interface.md) pro modul CLR (Common Language Runtime), který se použije jako semafor pro události čekání.</span><span class="sxs-lookup"><span data-stu-id="26640-103">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26640-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26640-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26640-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26640-105">Parameters</span></span>  
 `dwInitial`  
 <span data-ttu-id="26640-106">pro Počáteční počet pro `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="26640-106">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="26640-107">pro Maximální počet pro `ppSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="26640-107">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="26640-108">mimo Ukazatel na adresu `IHostSemaphore` instance nebo hodnotu null, pokud semafor nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="26640-108">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26640-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26640-109">Return Value</span></span>  
  
|<span data-ttu-id="26640-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26640-110">HRESULT</span></span>|<span data-ttu-id="26640-111">Popis</span><span class="sxs-lookup"><span data-stu-id="26640-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26640-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="26640-112">S_OK</span></span>|<span data-ttu-id="26640-113">`CreateSemaphore`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="26640-113">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="26640-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26640-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26640-115">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="26640-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26640-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26640-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26640-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="26640-117">The call timed out.</span></span>|  
|<span data-ttu-id="26640-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26640-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26640-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="26640-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26640-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26640-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26640-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="26640-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26640-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26640-122">E_FAIL</span></span>|<span data-ttu-id="26640-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="26640-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26640-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="26640-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26640-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26640-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="26640-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="26640-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="26640-127">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="26640-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26640-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26640-128">Remarks</span></span>  
 <span data-ttu-id="26640-129">`CreateSemaphore`zrcadlí funkci Win32, která má stejný název.</span><span class="sxs-lookup"><span data-stu-id="26640-129">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="26640-130">`dwInitial`Parametry a `dwMax` používají stejnou sémantiku pro počet semaforu jako Win32 `lInitialCount` a `lMaximumCount` parametry v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="26640-130">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="26640-131">`dwInitial`musí být v rozmezí od nuly do ( `dwMax` včetně).</span><span class="sxs-lookup"><span data-stu-id="26640-131">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="26640-132">`dwMax`musí být větší než nula.</span><span class="sxs-lookup"><span data-stu-id="26640-132">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26640-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26640-133">Requirements</span></span>  
 <span data-ttu-id="26640-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26640-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26640-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26640-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26640-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26640-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26640-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26640-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26640-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="26640-138">See also</span></span>

- [<span data-ttu-id="26640-139">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26640-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="26640-140">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26640-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="26640-141">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26640-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
