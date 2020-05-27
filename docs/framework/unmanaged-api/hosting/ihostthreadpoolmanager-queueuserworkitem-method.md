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
ms.openlocfilehash: b3d77e30cd48310c392d38dc29f62fab565c8b42
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842462"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="8d8e8-102">IHostThreadPoolManager::QueueUserWorkItem – metoda</span><span class="sxs-lookup"><span data-stu-id="8d8e8-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="8d8e8-103">Zařadí funkci do fronty pro spuštění a určí objekt obsahující data, která má tato funkce používat.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="8d8e8-104">Funkce se spustí, když bude vlákno k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d8e8-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d8e8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d8e8-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="8d8e8-107">pro Ukazatel na funkci, který představuje funkci, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="8d8e8-108">pro Objekt obsahující data, která mají být použita v `Function` .</span><span class="sxs-lookup"><span data-stu-id="8d8e8-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="8d8e8-109">pro Jedna z hodnot příznaků, jak je definována pro metodu Win32 `QueueUserWorkItem` , které řídí provádění.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d8e8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8d8e8-110">Return Value</span></span>  
  
|<span data-ttu-id="8d8e8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d8e8-111">HRESULT</span></span>|<span data-ttu-id="8d8e8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8d8e8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d8e8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d8e8-113">S_OK</span></span>|<span data-ttu-id="8d8e8-114">`QueueUserWorkItem`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="8d8e8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d8e8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d8e8-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d8e8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d8e8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d8e8-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-118">The call timed out.</span></span>|  
|<span data-ttu-id="8d8e8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d8e8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d8e8-120">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d8e8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d8e8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d8e8-122">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d8e8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d8e8-123">E_FAIL</span></span>|<span data-ttu-id="8d8e8-124">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d8e8-125">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d8e8-126">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d8e8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d8e8-127">Remarks</span></span>  
 <span data-ttu-id="8d8e8-128">`QueueUserWorkItem`zařadí pracovní položku do fronty v pracovním vlákně ve fondu vláken.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="8d8e8-129">Jeho signatura a typy parametrů jsou stejné jako odpovídající funkce Win32, která má stejný název.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="8d8e8-130">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="8d8e8-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d8e8-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d8e8-131">Requirements</span></span>  
 <span data-ttu-id="8d8e8-132">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d8e8-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d8e8-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8d8e8-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d8e8-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d8e8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d8e8-135">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8e8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8e8-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d8e8-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="8d8e8-137">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d8e8-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
