---
title: IHostMAlloc::DebugAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 3f85e7c7fd54079ddce37f739a3a7bc0fa830d31
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493289"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="d02d6-102">IHostMAlloc::DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="d02d6-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="d02d6-103">Požaduje, aby hostitel přidělil určenou velikost paměti z haldy a dále sledoval, kde byla paměť přidělena.</span><span class="sxs-lookup"><span data-stu-id="d02d6-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d02d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d02d6-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d02d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d02d6-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="d02d6-106">pro Velikost aktuální žádosti o přidělení paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="d02d6-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="d02d6-107">pro Jedna z hodnot [EMemoryCriticalLevel –](ememorycriticallevel-enumeration.md) , která indikuje dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="d02d6-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="d02d6-108">pro Soubor kódu spustitelného souboru, který se má ladit.</span><span class="sxs-lookup"><span data-stu-id="d02d6-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="d02d6-109">pro Číslo řádku, ve `pszFileName` kterém bylo přidělení požadováno.</span><span class="sxs-lookup"><span data-stu-id="d02d6-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="d02d6-110">mimo Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nebylo možné dokončit.</span><span class="sxs-lookup"><span data-stu-id="d02d6-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d02d6-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d02d6-111">Return Value</span></span>  
  
|<span data-ttu-id="d02d6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d02d6-112">HRESULT</span></span>|<span data-ttu-id="d02d6-113">Description</span><span class="sxs-lookup"><span data-stu-id="d02d6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d02d6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d02d6-114">S_OK</span></span>|<span data-ttu-id="d02d6-115">`DebugAlloc`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d02d6-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="d02d6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d02d6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d02d6-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d02d6-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d02d6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d02d6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d02d6-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d02d6-119">The call timed out.</span></span>|  
|<span data-ttu-id="d02d6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d02d6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d02d6-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d02d6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d02d6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d02d6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d02d6-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d02d6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d02d6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d02d6-124">E_FAIL</span></span>|<span data-ttu-id="d02d6-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d02d6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d02d6-126">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d02d6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d02d6-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d02d6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d02d6-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d02d6-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d02d6-129">K dokončení žádosti o přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="d02d6-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d02d6-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d02d6-130">Remarks</span></span>  
 <span data-ttu-id="d02d6-131">CLR získá ukazatel rozhraní na instanci [IHostMalloc](ihostmalloc-interface.md) voláním metody [IHostMemoryManager:: CreateMalloc –](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d02d6-131">The CLR gets an interface pointer to an [IHostMalloc](ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="d02d6-132">`DebugAlloc`umožňuje modulu runtime získat informace o souboru kódu pro použití během ladění.</span><span class="sxs-lookup"><span data-stu-id="d02d6-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d02d6-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d02d6-133">Requirements</span></span>  
 <span data-ttu-id="d02d6-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d02d6-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d02d6-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d02d6-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d02d6-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d02d6-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d02d6-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d02d6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02d6-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d02d6-138">See also</span></span>

- [<span data-ttu-id="d02d6-139">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d02d6-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="d02d6-140">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d02d6-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
