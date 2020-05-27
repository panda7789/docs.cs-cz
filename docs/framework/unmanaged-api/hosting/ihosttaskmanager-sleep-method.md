---
title: IHostTaskManager::Sleep – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: bb12547155383bb410f592018232ca6f688bab8a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841903"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="25250-102">IHostTaskManager::Sleep – metoda</span><span class="sxs-lookup"><span data-stu-id="25250-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="25250-103">Upozorní hostitele, že aktuální úloha přejde do režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="25250-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25250-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25250-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25250-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25250-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="25250-106">pro Časový interval v milisekundách, po který bude vlákno v režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="25250-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="25250-107">pro Jedna z hodnot výčtu [WAIT_OPTION](wait-option-enumeration.md) , která určuje, jakou akci má hostitel provést, pokud tato akce zablokuje.</span><span class="sxs-lookup"><span data-stu-id="25250-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25250-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="25250-108">Return Value</span></span>  
  
|<span data-ttu-id="25250-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25250-109">HRESULT</span></span>|<span data-ttu-id="25250-110">Popis</span><span class="sxs-lookup"><span data-stu-id="25250-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25250-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="25250-111">S_OK</span></span>|<span data-ttu-id="25250-112">`Sleep`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="25250-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="25250-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25250-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25250-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="25250-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25250-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25250-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25250-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="25250-116">The call timed out.</span></span>|  
|<span data-ttu-id="25250-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25250-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25250-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="25250-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25250-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25250-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25250-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="25250-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25250-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25250-121">E_FAIL</span></span>|<span data-ttu-id="25250-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="25250-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25250-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="25250-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25250-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="25250-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25250-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25250-125">Remarks</span></span>  
 <span data-ttu-id="25250-126">CLR obvykle volá `IHostTaskManager::Sleep` , když <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> je volána z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="25250-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25250-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25250-127">Requirements</span></span>  
 <span data-ttu-id="25250-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25250-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25250-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25250-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25250-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25250-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25250-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25250-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25250-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="25250-132">See also</span></span>

- [<span data-ttu-id="25250-133">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25250-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="25250-134">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25250-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="25250-135">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25250-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="25250-136">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25250-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
