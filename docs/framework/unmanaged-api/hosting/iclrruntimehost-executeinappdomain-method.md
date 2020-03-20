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
ms.openlocfilehash: c012e4e2b5e41737f7bbe6a0fb887693b0ba22c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176419"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="aef72-102">ICLRRuntimeHost::ExecuteInAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="aef72-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="aef72-103">Určuje, <xref:System.AppDomain> ve kterém má být zadaný spravovaný kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="aef72-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aef72-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aef72-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="aef72-106">[v] Číselné ID, <xref:System.AppDomain> ve kterém chcete provést zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="aef72-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="aef72-107">[v] Ukazatel na funkci, která má <xref:System.AppDomain>být spuštěna v rámci zadaného .</span><span class="sxs-lookup"><span data-stu-id="aef72-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="aef72-108">[v] Ukazatel na neprůhlednou paměť přidělenou volajícím.</span><span class="sxs-lookup"><span data-stu-id="aef72-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="aef72-109">Tento parametr je předán běžným jazykem runtime (CLR) zpětnému volání domény.</span><span class="sxs-lookup"><span data-stu-id="aef72-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="aef72-110">Není paměť haldy spravované za běhu; přidělení a životnost této paměti jsou řízeny volajícím.</span><span class="sxs-lookup"><span data-stu-id="aef72-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aef72-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aef72-111">Return Value</span></span>  
  
|<span data-ttu-id="aef72-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aef72-112">HRESULT</span></span>|<span data-ttu-id="aef72-113">Popis</span><span class="sxs-lookup"><span data-stu-id="aef72-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aef72-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="aef72-114">S_OK</span></span>|<span data-ttu-id="aef72-115">`ExecuteInAppDomain`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="aef72-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="aef72-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aef72-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aef72-117">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="aef72-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aef72-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aef72-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aef72-119">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="aef72-119">The call timed out.</span></span>|  
|<span data-ttu-id="aef72-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aef72-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aef72-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="aef72-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aef72-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aef72-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aef72-123">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="aef72-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aef72-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="aef72-124">E_FAIL</span></span>|<span data-ttu-id="aef72-125">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="aef72-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aef72-126">Pokud metoda vrátí E_FAIL, CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="aef72-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aef72-127">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aef72-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aef72-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aef72-128">Remarks</span></span>  
 <span data-ttu-id="aef72-129">`ExecuteInAppDomain`umožňuje hostiteli vykonávat kontrolu <xref:System.AppDomain> nad tím, který spravovaný zadaný spravovaný metoda by měla být provedena v.</span><span class="sxs-lookup"><span data-stu-id="aef72-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="aef72-130">Můžete získat hodnotu identifikátoru domény aplikace, která odpovídá hodnotě <xref:System.AppDomain.Id%2A> vlastnosti, voláním [Metody GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="aef72-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef72-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aef72-131">Requirements</span></span>  
 <span data-ttu-id="aef72-132">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aef72-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aef72-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aef72-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aef72-134">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aef72-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aef72-135">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aef72-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef72-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="aef72-136">See also</span></span>

- [<span data-ttu-id="aef72-137">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aef72-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
