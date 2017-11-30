---
title: "IHostMAlloc::Free – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Free
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ac361f939a134aa6d2bc8b215c5d447b352466e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="0f3ed-102">IHostMAlloc::Free – metoda</span><span class="sxs-lookup"><span data-stu-id="0f3ed-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="0f3ed-103">Uvolní paměť, která byla přidělena pomocí [alokační](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f3ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f3ed-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f3ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f3ed-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="0f3ed-106">[v] Ukazatel na uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f3ed-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f3ed-107">Return Value</span></span>  
  
|<span data-ttu-id="0f3ed-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f3ed-108">HRESULT</span></span>|<span data-ttu-id="0f3ed-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0f3ed-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f3ed-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f3ed-110">S_OK</span></span>|<span data-ttu-id="0f3ed-111">`Free`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="0f3ed-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f3ed-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f3ed-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f3ed-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f3ed-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f3ed-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-115">The call timed out.</span></span>|  
|<span data-ttu-id="0f3ed-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f3ed-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f3ed-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f3ed-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f3ed-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f3ed-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f3ed-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f3ed-120">E_FAIL</span></span>|<span data-ttu-id="0f3ed-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f3ed-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f3ed-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0f3ed-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0f3ed-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0f3ed-125">Došlo pokusu o volné paměti, která nebyla přidělena prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f3ed-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f3ed-126">Remarks</span></span>  
 <span data-ttu-id="0f3ed-127">Pokud `pMem` parametr odkazuje na oblast paměti, která nebyla přidělena pomocí volání `Alloc`, hostitele by měla vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="0f3ed-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f3ed-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f3ed-128">Requirements</span></span>  
 <span data-ttu-id="0f3ed-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f3ed-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f3ed-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f3ed-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f3ed-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f3ed-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f3ed-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f3ed-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3ed-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f3ed-133">See Also</span></span>  
 [<span data-ttu-id="0f3ed-134">Ihostmemorymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f3ed-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="0f3ed-135">Ihostmalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f3ed-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
