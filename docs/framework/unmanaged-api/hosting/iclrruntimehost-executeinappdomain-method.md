---
title: ICLRRuntimeHost::ExecuteInAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: c847f177f48d72f28192d1efabe93c65a7b3f4b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120495"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="c17d5-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c17d5-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="c17d5-103">Určuje <xref:System.AppDomain>, ve kterém se má spustit zadaný spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c17d5-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c17d5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c17d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c17d5-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="c17d5-106">pro Číselné ID <xref:System.AppDomain>, ve kterém má být provedena zadaná metoda.</span><span class="sxs-lookup"><span data-stu-id="c17d5-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="c17d5-107">pro Ukazatel na funkci, která má být provedena v rámci zadaného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c17d5-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="c17d5-108">pro Ukazatel na neprůhlednou paměť přidělenou volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c17d5-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="c17d5-109">Tento parametr je předaný modulem CLR (Common Language Runtime) do zpětného volání domény.</span><span class="sxs-lookup"><span data-stu-id="c17d5-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="c17d5-110">Nejedná se o nespravovanou paměť haldy za běhu; přidělování i životnost této paměti jsou ovládány volajícím.</span><span class="sxs-lookup"><span data-stu-id="c17d5-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c17d5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c17d5-111">Return Value</span></span>  
  
|<span data-ttu-id="c17d5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c17d5-112">HRESULT</span></span>|<span data-ttu-id="c17d5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c17d5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c17d5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c17d5-114">S_OK</span></span>|<span data-ttu-id="c17d5-115">`ExecuteInAppDomain` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c17d5-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="c17d5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c17d5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c17d5-117">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c17d5-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c17d5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c17d5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c17d5-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c17d5-119">The call timed out.</span></span>|  
|<span data-ttu-id="c17d5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c17d5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c17d5-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c17d5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c17d5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c17d5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c17d5-123">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="c17d5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c17d5-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c17d5-124">E_FAIL</span></span>|<span data-ttu-id="c17d5-125">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c17d5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c17d5-126">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c17d5-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c17d5-127">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c17d5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c17d5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c17d5-128">Remarks</span></span>  
 <span data-ttu-id="c17d5-129">`ExecuteInAppDomain` umožňuje hostiteli převzít kontrolu nad tím, která spravovaná <xref:System.AppDomain> zadaná spravovaná metoda se má spustit v.</span><span class="sxs-lookup"><span data-stu-id="c17d5-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="c17d5-130">Můžete získat hodnotu identifikátoru domény aplikace, který odpovídá hodnotě vlastnosti <xref:System.AppDomain.Id%2A> voláním [metody GetCurrentAppDomainId –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="c17d5-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17d5-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c17d5-131">Requirements</span></span>  
 <span data-ttu-id="c17d5-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c17d5-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c17d5-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c17d5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c17d5-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c17d5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c17d5-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c17d5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17d5-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c17d5-136">See also</span></span>

- [<span data-ttu-id="c17d5-137">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c17d5-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
