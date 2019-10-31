---
title: IHostMAlloc::Free – metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: f7ae4e4cbb757edea242c57720baeb70ced5c428
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192058"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="22d62-102">IHostMAlloc::Free – metoda</span><span class="sxs-lookup"><span data-stu-id="22d62-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="22d62-103">Uvolňuje paměť, která byla přidělena pomocí funkce [přidělení](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22d62-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d62-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22d62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d62-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="22d62-106">pro Ukazatel na paměť, která má být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="22d62-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22d62-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22d62-107">Return Value</span></span>  
  
|<span data-ttu-id="22d62-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22d62-108">HRESULT</span></span>|<span data-ttu-id="22d62-109">Popis</span><span class="sxs-lookup"><span data-stu-id="22d62-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22d62-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="22d62-110">S_OK</span></span>|<span data-ttu-id="22d62-111">`Free` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="22d62-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="22d62-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22d62-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22d62-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="22d62-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22d62-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22d62-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22d62-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="22d62-115">The call timed out.</span></span>|  
|<span data-ttu-id="22d62-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22d62-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22d62-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="22d62-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22d62-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22d62-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22d62-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="22d62-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22d62-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22d62-120">E_FAIL</span></span>|<span data-ttu-id="22d62-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="22d62-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22d62-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="22d62-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22d62-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="22d62-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="22d62-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="22d62-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="22d62-125">Byl proveden pokus o uvolnění paměti, která nebyla přidělena prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="22d62-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22d62-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22d62-126">Remarks</span></span>  
 <span data-ttu-id="22d62-127">Pokud parametr `pMem` odkazuje na oblast paměti, která nebyla přidělena pomocí volání `Alloc`, hostitel by měl vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="22d62-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d62-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d62-128">Requirements</span></span>  
 <span data-ttu-id="22d62-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d62-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d62-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22d62-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22d62-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="22d62-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d62-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d62-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d62-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d62-133">See also</span></span>

- [<span data-ttu-id="22d62-134">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d62-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="22d62-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d62-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
