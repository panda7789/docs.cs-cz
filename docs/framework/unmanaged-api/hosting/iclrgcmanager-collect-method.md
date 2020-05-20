---
title: ICLRGCManager::Collect – metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: aa906e314c408b7653e611b07d7ad21d4519b715
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616980"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="eca2a-102">ICLRGCManager::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="eca2a-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="eca2a-103">Vynutí uvolňování paměti pro určenou generaci.</span><span class="sxs-lookup"><span data-stu-id="eca2a-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca2a-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eca2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eca2a-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="eca2a-106">pro Generace, která se má shromáždit</span><span class="sxs-lookup"><span data-stu-id="eca2a-106">[in] The generation to collect.</span></span> <span data-ttu-id="eca2a-107">Hodnota-1 vynutí kolekci všech generací.</span><span class="sxs-lookup"><span data-stu-id="eca2a-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eca2a-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eca2a-108">Return Value</span></span>  
  
|<span data-ttu-id="eca2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eca2a-109">HRESULT</span></span>|<span data-ttu-id="eca2a-110">Popis</span><span class="sxs-lookup"><span data-stu-id="eca2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eca2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eca2a-111">S_OK</span></span>|<span data-ttu-id="eca2a-112">`Collect`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="eca2a-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="eca2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eca2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eca2a-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="eca2a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eca2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eca2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eca2a-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="eca2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="eca2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eca2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eca2a-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="eca2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eca2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eca2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eca2a-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="eca2a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eca2a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eca2a-121">E_FAIL</span></span>|<span data-ttu-id="eca2a-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="eca2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eca2a-123">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="eca2a-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eca2a-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="eca2a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eca2a-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eca2a-125">Remarks</span></span>  
 <span data-ttu-id="eca2a-126">`Collect`Metoda vynutí, aby systém uvolňování paměti CLR prováděl shromažďování bez ohledu na jeho aktuální stav.</span><span class="sxs-lookup"><span data-stu-id="eca2a-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca2a-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eca2a-127">Requirements</span></span>  
 <span data-ttu-id="eca2a-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca2a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca2a-129">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eca2a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eca2a-130">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eca2a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eca2a-131">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca2a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca2a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="eca2a-132">See also</span></span>

- [<span data-ttu-id="eca2a-133">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="eca2a-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="eca2a-134">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="eca2a-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="eca2a-135">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca2a-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="eca2a-136">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eca2a-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="eca2a-137">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="eca2a-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="eca2a-138">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eca2a-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="eca2a-139">Hostování</span><span class="sxs-lookup"><span data-stu-id="eca2a-139">Hosting</span></span>](index.md)
