---
title: "ICLRRuntimeHost::ExecuteApplication – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b765f020bd15fa94fb18a6fd7d81cf66c534639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="f7af3-102">ICLRRuntimeHost::ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="f7af3-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="f7af3-103">Používá ve scénářích nasazení na základě manifest ClickOnce pro zadání aplikací, které chcete aktivovat. v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="f7af3-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="f7af3-104">Další informace o těchto scénářích najdete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="f7af3-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7af3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7af3-105">Syntax</span></span>  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7af3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7af3-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="f7af3-107">[v] Úplný název aplikace, jak jsou definovány pro <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="f7af3-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="f7af3-108">[v] Počet řetězců, které jsou součástí `ppwzManifestPaths` pole.</span><span class="sxs-lookup"><span data-stu-id="f7af3-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="f7af3-109">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="f7af3-109">[in] Optional.</span></span> <span data-ttu-id="f7af3-110">Pole řetězců obsahující manifestu cesty pro danou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f7af3-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="f7af3-111">[v] Počet řetězců, které jsou součástí `ppwzActivationData` pole.</span><span class="sxs-lookup"><span data-stu-id="f7af3-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="f7af3-112">[v] Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="f7af3-112">[in] Optional.</span></span> <span data-ttu-id="f7af3-113">Pole řetězců obsahující data aktivace aplikace, jako jsou části řetězce dotazu adresy URL pro aplikace nasazené prostřednictvím webu.</span><span class="sxs-lookup"><span data-stu-id="f7af3-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="f7af3-114">[out] Hodnota vrácená ze vstupního bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7af3-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7af3-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7af3-115">Return Value</span></span>  
  
|<span data-ttu-id="f7af3-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7af3-116">HRESULT</span></span>|<span data-ttu-id="f7af3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f7af3-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7af3-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7af3-118">S_OK</span></span>|<span data-ttu-id="f7af3-119">`ExecuteApplication`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f7af3-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="f7af3-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7af3-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7af3-121">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f7af3-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7af3-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7af3-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7af3-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f7af3-123">The call timed out.</span></span>|  
|<span data-ttu-id="f7af3-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7af3-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7af3-125">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f7af3-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7af3-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7af3-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7af3-127">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f7af3-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7af3-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7af3-128">E_FAIL</span></span>|<span data-ttu-id="f7af3-129">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f7af3-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7af3-130">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f7af3-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7af3-131">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7af3-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7af3-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7af3-132">Remarks</span></span>  
 <span data-ttu-id="f7af3-133">`ExecuteApplication`slouží k aktivaci aplikace ClickOnce v doméně nově vytvořená aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7af3-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="f7af3-134">`pReturnValue` Výstupní parametr je nastaven na hodnotu vrácenou aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7af3-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="f7af3-135">Pokud zadáte hodnotu null pro `pReturnValue`, `ExecuteApplication` neselže, ale nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7af3-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7af3-136">Nevolejte [metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda před voláním `ExecuteApplication` metoda aktivace na základě manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7af3-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="f7af3-137">Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody, které se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="f7af3-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7af3-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7af3-138">Requirements</span></span>  
 <span data-ttu-id="f7af3-139">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7af3-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7af3-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7af3-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7af3-141">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7af3-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7af3-142">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7af3-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7af3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7af3-143">See Also</span></span>  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [<span data-ttu-id="f7af3-144">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7af3-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="f7af3-145">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="f7af3-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [<span data-ttu-id="f7af3-146">Návod: Stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="f7af3-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
