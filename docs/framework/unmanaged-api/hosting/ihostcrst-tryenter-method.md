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
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130497"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="0594a-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="0594a-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="0594a-103">Pokusí se zadat kritickou část reprezentovanou aktuální instancí [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="0594a-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0594a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0594a-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0594a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0594a-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0594a-106">pro Jedna z hodnot [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , která určuje, jakou akci má hostitel provést, pokud operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="0594a-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="0594a-107">[out] `true`, jestli se dá zadat kritická část; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="0594a-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0594a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0594a-108">Return Value</span></span>  
  
|<span data-ttu-id="0594a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0594a-109">HRESULT</span></span>|<span data-ttu-id="0594a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="0594a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0594a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0594a-111">S_OK</span></span>|<span data-ttu-id="0594a-112">`TryEnter` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0594a-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="0594a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0594a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0594a-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0594a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0594a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0594a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0594a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0594a-116">The call timed out.</span></span>|  
|<span data-ttu-id="0594a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0594a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0594a-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0594a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0594a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0594a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0594a-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0594a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0594a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0594a-121">E_FAIL</span></span>|<span data-ttu-id="0594a-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0594a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0594a-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0594a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0594a-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0594a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0594a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0594a-125">Remarks</span></span>  
 <span data-ttu-id="0594a-126">`TryEnter` vrátí hodnotu okamžitě a označuje, zda volající vlákno zadalo kritickou část.</span><span class="sxs-lookup"><span data-stu-id="0594a-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="0594a-127">Tato metoda zrcadlí funkci Wind32 `TryEnterCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="0594a-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0594a-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0594a-128">Requirements</span></span>  
 <span data-ttu-id="0594a-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0594a-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0594a-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0594a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0594a-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0594a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0594a-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0594a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0594a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0594a-133">See also</span></span>

- [<span data-ttu-id="0594a-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0594a-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="0594a-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0594a-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="0594a-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0594a-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
