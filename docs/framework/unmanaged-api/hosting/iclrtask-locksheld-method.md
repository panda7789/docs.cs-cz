---
title: ICLRTask::LocksHeld – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: c67f00acd61d6e0cdf3adfa0d3d0fda2a06a6f31
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762978"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="1b1c7-102">ICLRTask::LocksHeld – metoda</span><span class="sxs-lookup"><span data-stu-id="1b1c7-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="1b1c7-103">Získá počet zámků, které jsou aktuálně uchovávány na úkolu.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b1c7-104">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b1c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1b1c7-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="1b1c7-106">mimo Počet zámků uložených na úloze v době volání metody.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b1c7-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1b1c7-107">Return Value</span></span>  
  
|<span data-ttu-id="1b1c7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b1c7-108">HRESULT</span></span>|<span data-ttu-id="1b1c7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1b1c7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b1c7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b1c7-110">S_OK</span></span>|<span data-ttu-id="1b1c7-111">`LocksHeld`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="1b1c7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b1c7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b1c7-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b1c7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b1c7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b1c7-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-115">The call timed out.</span></span>|  
|<span data-ttu-id="1b1c7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b1c7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b1c7-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b1c7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b1c7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b1c7-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b1c7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b1c7-120">E_FAIL</span></span>|<span data-ttu-id="1b1c7-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b1c7-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b1c7-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b1c7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b1c7-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1b1c7-124">Requirements</span></span>  
 <span data-ttu-id="1b1c7-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1c7-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1c7-126">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1b1c7-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b1c7-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b1c7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b1c7-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1c7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1c7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b1c7-129">See also</span></span>

- [<span data-ttu-id="1b1c7-130">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1c7-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1b1c7-131">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1c7-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1b1c7-132">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1c7-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1b1c7-133">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1b1c7-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
