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
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804921"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="d5d0c-102">IHostCrst::Enter – metoda</span><span class="sxs-lookup"><span data-stu-id="d5d0c-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="d5d0c-103">Vstupuje do kritického oddílu, který je reprezentován aktuální instancí [IHostCrst](ihostcrst-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5d0c-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5d0c-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5d0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5d0c-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="d5d0c-106">pro Jedna z hodnot [WAIT_OPTION](wait-option-enumeration.md) určuje, jakou akci má hostitel provést, pokud operace zablokuje.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5d0c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5d0c-107">Return Value</span></span>  
  
|<span data-ttu-id="d5d0c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5d0c-108">HRESULT</span></span>|<span data-ttu-id="d5d0c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d5d0c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5d0c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5d0c-110">S_OK</span></span>|<span data-ttu-id="d5d0c-111">`Enter`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="d5d0c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5d0c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5d0c-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5d0c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5d0c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5d0c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-115">The call timed out.</span></span>|  
|<span data-ttu-id="d5d0c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5d0c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5d0c-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5d0c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5d0c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5d0c-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5d0c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5d0c-120">E_FAIL</span></span>|<span data-ttu-id="d5d0c-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5d0c-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5d0c-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5d0c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5d0c-124">Remarks</span></span>  
 <span data-ttu-id="d5d0c-125">`Enter`zrcadlí `EnterCriticalSection` funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5d0c-126">Tato metoda nevrátí do zadání kritického oddílu.</span><span class="sxs-lookup"><span data-stu-id="d5d0c-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d0c-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5d0c-127">Requirements</span></span>  
 <span data-ttu-id="d5d0c-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5d0c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d0c-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5d0c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5d0c-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5d0c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5d0c-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d0c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d0c-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5d0c-132">See also</span></span>

- [<span data-ttu-id="d5d0c-133">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5d0c-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="d5d0c-134">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5d0c-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="d5d0c-135">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5d0c-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
