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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18b4ad9590b57b629587af8f421a3f5902e5527f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704027"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="b7ffe-102">IHostMemoryManager::GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="b7ffe-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="b7ffe-103">Získá množství fyzické paměti, který je aktuálně používán a proto není dostupné jako ohlášené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ffe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7ffe-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7ffe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7ffe-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="b7ffe-106">[out] Ukazatel na přibližné procentuální hodnotu celkové velikosti fyzické paměti, která se právě používá.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="b7ffe-107">[out] Ukazatel na počet bajtů, které jsou k dispozici pro modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="b7ffe-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7ffe-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b7ffe-108">Return Value</span></span>  
  
|<span data-ttu-id="b7ffe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7ffe-109">HRESULT</span></span>|<span data-ttu-id="b7ffe-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b7ffe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7ffe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7ffe-111">S_OK</span></span>|<span data-ttu-id="b7ffe-112">`GetMemoryLoad` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="b7ffe-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7ffe-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7ffe-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7ffe-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7ffe-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7ffe-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-116">The call timed out.</span></span>|  
|<span data-ttu-id="b7ffe-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7ffe-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7ffe-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7ffe-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7ffe-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7ffe-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7ffe-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7ffe-121">E_FAIL</span></span>|<span data-ttu-id="b7ffe-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7ffe-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7ffe-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7ffe-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7ffe-125">Remarks</span></span>  
 <span data-ttu-id="b7ffe-126">`GetMemoryLoad` zabalí rozhraní Win32 `GlobalMemoryStatus` funkce.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="b7ffe-127">Hodnota `pMemoryLoad` odpovídá `dwMemoryLoad` pole `MEMORYSTATUS` struktura vrácená z `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="b7ffe-128">Modul runtime používá vrácenou hodnotu jako heuristické metody pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="b7ffe-129">Například pokud hostitel hlásí, že většina paměti se používá, systému uvolňování paměti může rozhodnout, jestli mají být shromažďovány z více generací zvýšit množství paměti, která se dá potenciálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b7ffe-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ffe-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7ffe-130">Requirements</span></span>  
 <span data-ttu-id="b7ffe-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ffe-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ffe-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7ffe-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7ffe-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7ffe-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7ffe-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ffe-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ffe-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7ffe-135">See also</span></span>
- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="b7ffe-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b7ffe-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
