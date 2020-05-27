---
title: IHostIoCompletionManager::Bind – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 8d18e6c1dca7f52b17c19f4638410a08866905f7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804802"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="96cf1-102">IHostIoCompletionManager::Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="96cf1-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="96cf1-103">Váže zadaný popisovač na port pro dokončení I/O, který byl vytvořen dřívějším voláním [CreateIoCompletionPort –](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="96cf1-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96cf1-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96cf1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96cf1-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="96cf1-106">pro Port dokončení I/O, ke kterému se má vytvořit vazba `hHandle` .</span><span class="sxs-lookup"><span data-stu-id="96cf1-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="96cf1-107">Pokud je hodnota `hPort` null, `hHandle` je svázána s výchozím portem pro dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="96cf1-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="96cf1-108">pro Popisovač operačního systému, k němuž má být vytvořena vazba `hPort` .</span><span class="sxs-lookup"><span data-stu-id="96cf1-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96cf1-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="96cf1-109">Return Value</span></span>  
  
|<span data-ttu-id="96cf1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96cf1-110">HRESULT</span></span>|<span data-ttu-id="96cf1-111">Popis</span><span class="sxs-lookup"><span data-stu-id="96cf1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96cf1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="96cf1-112">S_OK</span></span>|<span data-ttu-id="96cf1-113">`Bind`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="96cf1-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="96cf1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96cf1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96cf1-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="96cf1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96cf1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96cf1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96cf1-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="96cf1-117">The call timed out.</span></span>|  
|<span data-ttu-id="96cf1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96cf1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96cf1-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="96cf1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96cf1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96cf1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96cf1-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="96cf1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96cf1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96cf1-122">E_FAIL</span></span>|<span data-ttu-id="96cf1-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="96cf1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96cf1-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="96cf1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96cf1-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="96cf1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96cf1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96cf1-126">Remarks</span></span>  
 <span data-ttu-id="96cf1-127">Port pro dokončení I/O se vytvoří pomocí volání `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="96cf1-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="96cf1-128">CLR volá `Bind` k navázání popisovače na tento port.</span><span class="sxs-lookup"><span data-stu-id="96cf1-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96cf1-129">Po dokončení vstupně-výstupních požadavků musí hostitel zavolat metodu [ICLRIoCompletionManager –:: doplněné](iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="96cf1-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96cf1-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96cf1-130">Requirements</span></span>  
 <span data-ttu-id="96cf1-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96cf1-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96cf1-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="96cf1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96cf1-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="96cf1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96cf1-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96cf1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96cf1-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="96cf1-135">See also</span></span>

- [<span data-ttu-id="96cf1-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96cf1-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
