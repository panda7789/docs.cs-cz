---
title: IHostCrst::Enter – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc597e741023af1c7cc1f48e378083157dd4a5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937743"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="2d40f-102">IHostCrst::Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="2d40f-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="2d40f-103">Vstupuje do kritického oddílu, který je reprezentován aktuální instancí [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2d40f-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d40f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d40f-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d40f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d40f-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="2d40f-106">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , která určuje, jakou akci má hostitel provést, pokud operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="2d40f-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d40f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d40f-107">Return Value</span></span>  
  
|<span data-ttu-id="2d40f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d40f-108">HRESULT</span></span>|<span data-ttu-id="2d40f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2d40f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d40f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d40f-110">S_OK</span></span>|<span data-ttu-id="2d40f-111">`Enter`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2d40f-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="2d40f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d40f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d40f-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2d40f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d40f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d40f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d40f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2d40f-115">The call timed out.</span></span>|  
|<span data-ttu-id="2d40f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d40f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d40f-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2d40f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d40f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d40f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d40f-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2d40f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d40f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d40f-120">E_FAIL</span></span>|<span data-ttu-id="2d40f-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2d40f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d40f-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2d40f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d40f-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d40f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d40f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d40f-124">Remarks</span></span>  
 <span data-ttu-id="2d40f-125">`Enter`zrcadlí funkci `EnterCriticalSection` Win32.</span><span class="sxs-lookup"><span data-stu-id="2d40f-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d40f-126">Tato metoda nevrátí do zadání kritického oddílu.</span><span class="sxs-lookup"><span data-stu-id="2d40f-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d40f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d40f-127">Requirements</span></span>  
 <span data-ttu-id="2d40f-128">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d40f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d40f-129">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d40f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d40f-130">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d40f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d40f-131">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d40f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d40f-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d40f-132">See also</span></span>

- [<span data-ttu-id="2d40f-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d40f-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="2d40f-134">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d40f-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="2d40f-135">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d40f-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
