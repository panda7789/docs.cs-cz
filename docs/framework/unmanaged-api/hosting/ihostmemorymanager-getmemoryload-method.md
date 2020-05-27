---
title: IHostMemoryManager::GetMemoryLoad – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 73d9ae865b2c971a4defcacf5bd6505836c74e02
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804496"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="dd265-102">IHostMemoryManager::GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="dd265-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="dd265-103">Získá velikost fyzické paměti, která je právě používána, a proto není k dispozici, jak je uvedeno v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="dd265-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd265-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd265-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd265-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd265-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="dd265-106">mimo Ukazatel na přibližnou procentuální hodnotu celkové fyzické paměti, která se právě používá.</span><span class="sxs-lookup"><span data-stu-id="dd265-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="dd265-107">mimo Ukazatel na počet bajtů dostupných pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="dd265-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd265-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dd265-108">Return Value</span></span>  
  
|<span data-ttu-id="dd265-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd265-109">HRESULT</span></span>|<span data-ttu-id="dd265-110">Popis</span><span class="sxs-lookup"><span data-stu-id="dd265-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd265-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd265-111">S_OK</span></span>|<span data-ttu-id="dd265-112">`GetMemoryLoad`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dd265-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="dd265-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd265-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd265-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dd265-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dd265-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dd265-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dd265-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dd265-116">The call timed out.</span></span>|  
|<span data-ttu-id="dd265-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dd265-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dd265-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="dd265-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dd265-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dd265-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dd265-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="dd265-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dd265-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd265-121">E_FAIL</span></span>|<span data-ttu-id="dd265-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="dd265-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dd265-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="dd265-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dd265-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd265-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd265-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd265-125">Remarks</span></span>  
 <span data-ttu-id="dd265-126">`GetMemoryLoad`zabalí funkci Win32 `GlobalMemoryStatus` .</span><span class="sxs-lookup"><span data-stu-id="dd265-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="dd265-127">Hodnota `pMemoryLoad` je ekvivalentem `dwMemoryLoad` pole ve `MEMORYSTATUS` struktuře vrácené z `GlobalMemoryStatus` .</span><span class="sxs-lookup"><span data-stu-id="dd265-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="dd265-128">Modul runtime používá návratovou hodnotu jako heuristickou pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="dd265-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="dd265-129">Například pokud hostitel hlásí, že je většina paměti používána, systém uvolňování paměti se může rozhodnout shromáždit z více generací a zvýšit tak množství paměti, které může být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="dd265-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd265-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd265-130">Requirements</span></span>  
 <span data-ttu-id="dd265-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd265-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd265-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd265-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd265-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd265-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd265-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd265-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd265-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd265-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="dd265-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd265-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
