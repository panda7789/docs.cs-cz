---
title: IHostThreadPoolManager::QueueUserWorkItem – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12c571f478f15a0b72168977f12623be1c4a08a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749157"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="b5999-102">IHostThreadPoolManager::QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="b5999-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="b5999-103">Zařadí do fronty pro spuštění funkce a určuje objekt, který obsahuje data pro tuto funkci používat.</span><span class="sxs-lookup"><span data-stu-id="b5999-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="b5999-104">Funkce se provede při vlákno nebude k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b5999-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5999-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5999-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5999-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5999-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="b5999-107">[in] Ukazatel na funkci, která představuje funkce pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="b5999-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="b5999-108">[in] Objekt, který obsahuje data používané `Function`.</span><span class="sxs-lookup"><span data-stu-id="b5999-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="b5999-109">[in] Příznaky hodnoty, jak jsou definovány pro Win32 `QueueUserWorkItem` metody, které řídí zpracování.</span><span class="sxs-lookup"><span data-stu-id="b5999-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5999-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b5999-110">Return Value</span></span>  
  
|<span data-ttu-id="b5999-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5999-111">HRESULT</span></span>|<span data-ttu-id="b5999-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b5999-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5999-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5999-113">S_OK</span></span>|<span data-ttu-id="b5999-114">`QueueUserWorkItem` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b5999-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="b5999-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b5999-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b5999-116">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b5999-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b5999-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b5999-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b5999-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b5999-118">The call timed out.</span></span>|  
|<span data-ttu-id="b5999-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b5999-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b5999-120">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="b5999-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b5999-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b5999-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b5999-122">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="b5999-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b5999-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b5999-123">E_FAIL</span></span>|<span data-ttu-id="b5999-124">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="b5999-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b5999-125">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b5999-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b5999-126">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b5999-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5999-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5999-127">Remarks</span></span>  
 <span data-ttu-id="b5999-128">`QueueUserWorkItem` zařadí do fronty pracovní položku k pracovní podproces ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="b5999-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="b5999-129">Jeho podpis a parametr typy jsou stejné jako odpovídající funkce Win32, který má stejný název.</span><span class="sxs-lookup"><span data-stu-id="b5999-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="b5999-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="b5999-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5999-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5999-131">Requirements</span></span>  
 <span data-ttu-id="b5999-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5999-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5999-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b5999-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5999-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5999-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5999-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5999-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5999-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5999-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b5999-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b5999-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
