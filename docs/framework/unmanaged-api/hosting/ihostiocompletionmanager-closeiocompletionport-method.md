---
title: IHostIoCompletionManager::CloseIoCompletionPort – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: 5e2e49b4c993e127a31b54d40f721e0714198780
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804777"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="74513-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="74513-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="74513-103">Požaduje, aby hostitel zavřel port, který byl otevřen prostřednictvím dřívějšího volání [CreateIoCompletionPort –](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="74513-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74513-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74513-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74513-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74513-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="74513-106">pro Popisovač portu, který má být zavřen.</span><span class="sxs-lookup"><span data-stu-id="74513-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74513-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74513-107">Return Value</span></span>  
  
|<span data-ttu-id="74513-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74513-108">HRESULT</span></span>|<span data-ttu-id="74513-109">Popis</span><span class="sxs-lookup"><span data-stu-id="74513-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74513-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="74513-110">S_OK</span></span>|<span data-ttu-id="74513-111">`CloseIoCompletionPort`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="74513-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="74513-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="74513-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="74513-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="74513-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="74513-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="74513-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="74513-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="74513-115">The call timed out.</span></span>|  
|<span data-ttu-id="74513-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="74513-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="74513-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="74513-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="74513-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="74513-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="74513-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="74513-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="74513-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="74513-120">E_FAIL</span></span>|<span data-ttu-id="74513-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="74513-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="74513-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="74513-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="74513-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="74513-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="74513-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="74513-124">E_INVALIDARG</span></span>|<span data-ttu-id="74513-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="74513-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74513-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74513-126">Remarks</span></span>  
 <span data-ttu-id="74513-127">`hPort`musí být popisovačem portu, který byl vytvořen starším voláním metody `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="74513-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74513-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74513-128">Requirements</span></span>  
 <span data-ttu-id="74513-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74513-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74513-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74513-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74513-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="74513-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74513-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74513-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74513-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="74513-133">See also</span></span>

- [<span data-ttu-id="74513-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74513-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="74513-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74513-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
