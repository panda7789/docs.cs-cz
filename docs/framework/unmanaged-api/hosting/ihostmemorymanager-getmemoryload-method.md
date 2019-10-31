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
ms.openlocfilehash: 2210dcd9e8a8af92b7905ec680c53c1119e6a3cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136709"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="7b107-102">IHostMemoryManager::GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="7b107-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="7b107-103">Získá velikost fyzické paměti, která je právě používána, a proto není k dispozici, jak je uvedeno v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="7b107-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b107-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b107-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b107-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b107-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="7b107-106">mimo Ukazatel na přibližnou procentuální hodnotu celkové fyzické paměti, která se právě používá.</span><span class="sxs-lookup"><span data-stu-id="7b107-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="7b107-107">mimo Ukazatel na počet bajtů dostupných pro modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7b107-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b107-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7b107-108">Return Value</span></span>  
  
|<span data-ttu-id="7b107-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b107-109">HRESULT</span></span>|<span data-ttu-id="7b107-110">Popis</span><span class="sxs-lookup"><span data-stu-id="7b107-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b107-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b107-111">S_OK</span></span>|<span data-ttu-id="7b107-112">`GetMemoryLoad` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7b107-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="7b107-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b107-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b107-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7b107-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7b107-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7b107-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7b107-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7b107-116">The call timed out.</span></span>|  
|<span data-ttu-id="7b107-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7b107-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7b107-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7b107-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7b107-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7b107-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7b107-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7b107-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7b107-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b107-121">E_FAIL</span></span>|<span data-ttu-id="7b107-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7b107-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7b107-123">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7b107-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7b107-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7b107-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b107-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b107-125">Remarks</span></span>  
 <span data-ttu-id="7b107-126">`GetMemoryLoad` zabalí funkci Win32 `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="7b107-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="7b107-127">Hodnota `pMemoryLoad` je ekvivalentem pole `dwMemoryLoad` ve struktuře `MEMORYSTATUS` vrácených z `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="7b107-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="7b107-128">Modul runtime používá návratovou hodnotu jako heuristickou pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7b107-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="7b107-129">Například pokud hostitel hlásí, že je většina paměti používána, systém uvolňování paměti se může rozhodnout shromáždit z více generací a zvýšit tak množství paměti, které může být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7b107-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b107-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b107-130">Requirements</span></span>  
 <span data-ttu-id="7b107-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b107-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b107-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7b107-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b107-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7b107-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b107-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b107-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b107-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b107-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="7b107-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b107-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
