---
title: ICLRIoCompletionManager::OnComplete – metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703823"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="d6e30-102">ICLRIoCompletionManager::OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="d6e30-102">ICLRIoCompletionManager::OnComplete Method</span></span>
<span data-ttu-id="d6e30-103">Upozorňuje modul CLR (Common Language Runtime) na stav vstupně-výstupních požadavků, který byl proveden pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6e30-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6e30-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6e30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6e30-105">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="d6e30-106">pro Hodnota HRESULT, která indikuje stav operace vazby.</span><span class="sxs-lookup"><span data-stu-id="d6e30-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="d6e30-107">S_OK označuje, že operace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="d6e30-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="d6e30-108">HOST_E_INTERRUPTED označuje, že volání bylo ukončeno před dokončením.</span><span class="sxs-lookup"><span data-stu-id="d6e30-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="d6e30-109">E_FAIL označuje, že došlo k neznámé, neobnovitelné, závažné chybě.</span><span class="sxs-lookup"><span data-stu-id="d6e30-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="d6e30-110">pro Počet bajtů přenesených během zpracování vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="d6e30-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="d6e30-111">pro Ukazatel na `OVERLAPPED` strukturu, která byla předána volání `IHostIoCompletionManager::Bind` metody.</span><span class="sxs-lookup"><span data-stu-id="d6e30-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6e30-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6e30-112">Return Value</span></span>  
  
|<span data-ttu-id="d6e30-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6e30-113">HRESULT</span></span>|<span data-ttu-id="d6e30-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d6e30-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6e30-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6e30-115">S_OK</span></span>|<span data-ttu-id="d6e30-116">`OnComplete`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d6e30-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="d6e30-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6e30-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6e30-118">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d6e30-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6e30-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6e30-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6e30-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d6e30-120">The call timed out.</span></span>|  
|<span data-ttu-id="d6e30-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6e30-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6e30-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d6e30-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6e30-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6e30-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6e30-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d6e30-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6e30-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6e30-125">E_FAIL</span></span>|<span data-ttu-id="d6e30-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d6e30-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6e30-127">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="d6e30-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6e30-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d6e30-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6e30-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6e30-129">Remarks</span></span>  
 <span data-ttu-id="d6e30-130">Pokud hostitel implementuje abstrakci dokončení vstupně-výstupních operací, CLR vytvoří požadavky na vstupně-výstupní operace prostřednictvím hostitele pomocí metod [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d6e30-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="d6e30-131">Hostitel pak zavolá `OnComplete` metodu, která upozorní modul runtime na výsledek takových požadavků.</span><span class="sxs-lookup"><span data-stu-id="d6e30-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e30-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6e30-132">Requirements</span></span>  
 <span data-ttu-id="d6e30-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6e30-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e30-134">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6e30-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6e30-135">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d6e30-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6e30-136">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e30-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e30-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6e30-137">See also</span></span>

- [<span data-ttu-id="d6e30-138">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6e30-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d6e30-139">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6e30-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="d6e30-140">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6e30-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
