---
title: "IHostThreadPoolManager::QueueUserWorkItem – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.QueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0a304c2052192d3cba761a128e15dc463011030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="ff98e-102">IHostThreadPoolManager::QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="ff98e-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="ff98e-103">Fronty funkce pro spuštění a určuje objekt obsahující data, která má být používána této funkce.</span><span class="sxs-lookup"><span data-stu-id="ff98e-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="ff98e-104">Funkce provede, až vlákno k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ff98e-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff98e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff98e-105">Syntax</span></span>  
  
```  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff98e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff98e-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="ff98e-107">[v] Ukazatel na funkci, který představuje funkci provést.</span><span class="sxs-lookup"><span data-stu-id="ff98e-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="ff98e-108">[v] Objekt, který obsahuje data, která má být používána `Function`.</span><span class="sxs-lookup"><span data-stu-id="ff98e-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="ff98e-109">[v] Jeden z příznaků hodnoty, jak jsou definovány pro Win32 `QueueUserWorkItem` metoda, která řízení provádění.</span><span class="sxs-lookup"><span data-stu-id="ff98e-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff98e-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ff98e-110">Return Value</span></span>  
  
|<span data-ttu-id="ff98e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff98e-111">HRESULT</span></span>|<span data-ttu-id="ff98e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ff98e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff98e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff98e-113">S_OK</span></span>|<span data-ttu-id="ff98e-114">`QueueUserWorkItem`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ff98e-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="ff98e-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff98e-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff98e-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ff98e-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff98e-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff98e-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff98e-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ff98e-118">The call timed out.</span></span>|  
|<span data-ttu-id="ff98e-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff98e-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff98e-120">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="ff98e-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff98e-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff98e-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff98e-122">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="ff98e-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff98e-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff98e-123">E_FAIL</span></span>|<span data-ttu-id="ff98e-124">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="ff98e-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff98e-125">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ff98e-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff98e-126">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff98e-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff98e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff98e-127">Remarks</span></span>  
 <span data-ttu-id="ff98e-128">`QueueUserWorkItem`zařadí do fronty pracovní položku pro pracovní vlákno ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="ff98e-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="ff98e-129">Typy jejího podpisu a parametru jsou stejné jako odpovídající funkce Win32, která má stejný název.</span><span class="sxs-lookup"><span data-stu-id="ff98e-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="ff98e-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="ff98e-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff98e-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff98e-131">Requirements</span></span>  
 <span data-ttu-id="ff98e-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff98e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff98e-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff98e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff98e-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff98e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff98e-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff98e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff98e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff98e-136">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="ff98e-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff98e-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
