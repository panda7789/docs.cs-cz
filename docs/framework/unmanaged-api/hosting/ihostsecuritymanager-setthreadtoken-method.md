---
title: IHostSecurityManager::SetThreadToken – metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: aa17f637ef71373697db5ce66e4a6540c5cc5fbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139491"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="d790d-102">IHostSecurityManager::SetThreadToken – metoda</span><span class="sxs-lookup"><span data-stu-id="d790d-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="d790d-103">Nastaví popisovač pro aktuálně prováděné vlákno.</span><span class="sxs-lookup"><span data-stu-id="d790d-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d790d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d790d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d790d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d790d-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="d790d-106">pro Popisovač tokenu, který se má nastavit pro aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="d790d-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d790d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d790d-107">Return Value</span></span>  
  
|<span data-ttu-id="d790d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d790d-108">HRESULT</span></span>|<span data-ttu-id="d790d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d790d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d790d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d790d-110">S_OK</span></span>|<span data-ttu-id="d790d-111">`SetThreadToken` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d790d-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="d790d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d790d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d790d-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d790d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d790d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d790d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d790d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d790d-115">The call timed out.</span></span>|  
|<span data-ttu-id="d790d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d790d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d790d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d790d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d790d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d790d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d790d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d790d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d790d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d790d-120">E_FAIL</span></span>|<span data-ttu-id="d790d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d790d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d790d-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d790d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d790d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d790d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d790d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d790d-124">Remarks</span></span>  
 <span data-ttu-id="d790d-125">`IHostSecurityManager::SetThreadToken` se chová podobně jako odpovídající funkce Win32 stejného názvu, s tím rozdílem, že funkce Win32 umožňuje volajícímu předat popisovač do libovolného vlákna, zatímco `IHostSecurityManager::SetThreadToken` může přidružit token pouze k aktuálně spuštěnému vláknu.</span><span class="sxs-lookup"><span data-stu-id="d790d-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="d790d-126">Typ `HANDLE` není kompatibilní s modelem COM; To znamená, že jeho velikost je specifická pro operační systém a vyžaduje vlastní zařazování.</span><span class="sxs-lookup"><span data-stu-id="d790d-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="d790d-127">Proto je tento token určen pouze pro použití v rámci procesu, mezi CLR a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d790d-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d790d-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d790d-128">Requirements</span></span>  
 <span data-ttu-id="d790d-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d790d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d790d-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d790d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d790d-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d790d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d790d-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d790d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d790d-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d790d-133">See also</span></span>

- [<span data-ttu-id="d790d-134">IHostSecurityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d790d-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="d790d-135">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d790d-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
