---
title: IHostCrst::TryEnter – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: 782a12a47de0196b90de06572520ef5ed36efb26
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804867"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="82219-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="82219-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="82219-103">Pokusí se zadat kritickou část reprezentovanou aktuální instancí [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="82219-103">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82219-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82219-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82219-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82219-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="82219-106">pro Jedna z hodnot [WAIT_OPTION](wait-option-enumeration.md) určuje, jakou akci má hostitel provést, pokud operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="82219-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="82219-107">[out] `true` Pokud je možné zadat kritickou část; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="82219-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82219-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="82219-108">Return Value</span></span>  
  
|<span data-ttu-id="82219-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82219-109">HRESULT</span></span>|<span data-ttu-id="82219-110">Popis</span><span class="sxs-lookup"><span data-stu-id="82219-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82219-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="82219-111">S_OK</span></span>|<span data-ttu-id="82219-112">`TryEnter`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="82219-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="82219-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82219-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82219-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="82219-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82219-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82219-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82219-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="82219-116">The call timed out.</span></span>|  
|<span data-ttu-id="82219-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82219-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82219-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="82219-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82219-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82219-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82219-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="82219-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82219-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82219-121">E_FAIL</span></span>|<span data-ttu-id="82219-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="82219-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82219-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="82219-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82219-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="82219-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82219-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82219-125">Remarks</span></span>  
 <span data-ttu-id="82219-126">`TryEnter`Vrátí hodnotu okamžitě a označuje, zda volající vlákno zadalo kritickou část.</span><span class="sxs-lookup"><span data-stu-id="82219-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="82219-127">Tato metoda zrcadlí `TryEnterCriticalSection` funkci Wind32.</span><span class="sxs-lookup"><span data-stu-id="82219-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82219-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82219-128">Requirements</span></span>  
 <span data-ttu-id="82219-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82219-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82219-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="82219-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82219-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82219-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82219-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82219-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82219-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="82219-133">See also</span></span>

- [<span data-ttu-id="82219-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82219-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="82219-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82219-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="82219-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82219-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
