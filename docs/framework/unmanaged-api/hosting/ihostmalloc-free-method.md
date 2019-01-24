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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 719c963d1627250da5f3705af9801dc287e1bb19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507242"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="bb879-102">IHostMAlloc::Free – metoda</span><span class="sxs-lookup"><span data-stu-id="bb879-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="bb879-103">Uvolnění paměti, která byla přidělena pomocí [alokační](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="bb879-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb879-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb879-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb879-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb879-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="bb879-106">[in] Ukazatel na paměť k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="bb879-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb879-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bb879-107">Return Value</span></span>  
  
|<span data-ttu-id="bb879-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb879-108">HRESULT</span></span>|<span data-ttu-id="bb879-109">Popis</span><span class="sxs-lookup"><span data-stu-id="bb879-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb879-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb879-110">S_OK</span></span>|<span data-ttu-id="bb879-111">`Free` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="bb879-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="bb879-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb879-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb879-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bb879-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb879-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb879-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb879-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bb879-115">The call timed out.</span></span>|  
|<span data-ttu-id="bb879-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb879-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb879-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="bb879-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb879-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb879-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb879-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="bb879-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb879-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb879-120">E_FAIL</span></span>|<span data-ttu-id="bb879-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="bb879-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb879-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="bb879-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb879-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bb879-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bb879-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bb879-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bb879-125">Byl proveden pokus o uvolnění paměti, který nebyl přidělen prostřednictvím hostitele.</span><span class="sxs-lookup"><span data-stu-id="bb879-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb879-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bb879-126">Remarks</span></span>  
 <span data-ttu-id="bb879-127">Pokud `pMem` parametr odkazuje na oblast paměti, který nebyl přidělen pomocí volání `Alloc`, hostitele by měl vrátit HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="bb879-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb879-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb879-128">Requirements</span></span>  
 <span data-ttu-id="bb879-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb879-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb879-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb879-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb879-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb879-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb879-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb879-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb879-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb879-133">See also</span></span>
- [<span data-ttu-id="bb879-134">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb879-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="bb879-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb879-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
