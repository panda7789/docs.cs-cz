---
title: IHostIoCompletionManager::GetAvailableThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 7ea7395bb1f185ba59940d76def562ab5440e560
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804756"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="846fc-102">IHostIoCompletionManager::GetAvailableThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="846fc-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>
<span data-ttu-id="846fc-103">Získá počet vláken dokončování v/v celkového počtu vláken spravovaných hostitelem, který aktuálně neobsluhuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="846fc-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="846fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="846fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="846fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="846fc-105">Parameters</span></span>  
 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="846fc-106">mimo Ukazatel na počet vstupně-výstupních vláken, která spravuje hostitel, kteří jsou aktuálně k dispozici pro žádosti o služby.</span><span class="sxs-lookup"><span data-stu-id="846fc-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="846fc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="846fc-107">Return Value</span></span>  
  
|<span data-ttu-id="846fc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="846fc-108">HRESULT</span></span>|<span data-ttu-id="846fc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="846fc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="846fc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="846fc-110">S_OK</span></span>|<span data-ttu-id="846fc-111">`GetAvailableThreads`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="846fc-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="846fc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="846fc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="846fc-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="846fc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="846fc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="846fc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="846fc-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="846fc-115">The call timed out.</span></span>|  
|<span data-ttu-id="846fc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="846fc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="846fc-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="846fc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="846fc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="846fc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="846fc-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="846fc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="846fc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="846fc-120">E_FAIL</span></span>|<span data-ttu-id="846fc-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="846fc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="846fc-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="846fc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="846fc-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="846fc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="846fc-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="846fc-124">E_NOTIMPL</span></span>|<span data-ttu-id="846fc-125">Hostitel neposkytuje implementaci `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="846fc-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="846fc-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="846fc-126">Remarks</span></span>  
 <span data-ttu-id="846fc-127">Hostitel může chtít exkluzivní kontrolu nad velikostí fondu vláken v/v dokončování z důvodů, jako je implementace, výkon nebo škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="846fc-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="846fc-128">Proto není nutné implementovat hostitele `GetAvailableThreads` .</span><span class="sxs-lookup"><span data-stu-id="846fc-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="846fc-129">V takovém případě by měl hostitel vracet E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="846fc-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="846fc-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="846fc-130">Requirements</span></span>  
 <span data-ttu-id="846fc-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="846fc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="846fc-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="846fc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="846fc-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="846fc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="846fc-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="846fc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="846fc-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="846fc-135">See also</span></span>

- [<span data-ttu-id="846fc-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="846fc-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="846fc-137">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="846fc-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
