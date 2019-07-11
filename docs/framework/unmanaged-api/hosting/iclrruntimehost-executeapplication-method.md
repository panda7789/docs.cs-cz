---
title: ICLRRuntimeHost::ExecuteApplication – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8db6fd1296420011dcbfbbb0e5682f8a484dc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768810"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="7d5aa-102">ICLRRuntimeHost::ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="7d5aa-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="7d5aa-103">Použít ve scénářích nasazení na bázi manifest ClickOnce k určení aktivovat v nové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="7d5aa-104">Další informace o těchto scénářích najdete v tématu [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="7d5aa-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d5aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d5aa-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d5aa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d5aa-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="7d5aa-107">[in] Úplný název aplikace, jak jsou definovány pro <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="7d5aa-108">[in] Počet součástí řetězce `ppwzManifestPaths` pole.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="7d5aa-109">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-109">[in] Optional.</span></span> <span data-ttu-id="7d5aa-110">Pole řetězců obsahující cesty k manifestu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="7d5aa-111">[in] Počet součástí řetězce `ppwzActivationData` pole.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="7d5aa-112">[in] Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-112">[in] Optional.</span></span> <span data-ttu-id="7d5aa-113">Pole řetězců obsahující data aktivace aplikace, jako je například část řetězec dotazu adresy URL pro aplikace nasazené prostřednictvím webu.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="7d5aa-114">[out] Hodnota vrácená ze vstupního bodu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d5aa-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d5aa-115">Return Value</span></span>  
  
|<span data-ttu-id="7d5aa-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d5aa-116">HRESULT</span></span>|<span data-ttu-id="7d5aa-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7d5aa-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d5aa-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d5aa-118">S_OK</span></span>|<span data-ttu-id="7d5aa-119">`ExecuteApplication` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="7d5aa-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d5aa-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d5aa-121">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d5aa-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d5aa-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d5aa-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-123">The call timed out.</span></span>|  
|<span data-ttu-id="7d5aa-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d5aa-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d5aa-125">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d5aa-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d5aa-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d5aa-127">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d5aa-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d5aa-128">E_FAIL</span></span>|<span data-ttu-id="7d5aa-129">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d5aa-130">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d5aa-131">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d5aa-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d5aa-132">Remarks</span></span>  
 <span data-ttu-id="7d5aa-133">`ExecuteApplication` slouží k aktivaci aplikací ClickOnce v doméně se nově vytvořená aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="7d5aa-134">`pReturnValue` Výstupní parametr je nastaven na hodnotu vrácenou příkazem aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="7d5aa-135">Pokud zadáte hodnotu null pro `pReturnValue`, `ExecuteApplication` není selže, ale nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d5aa-136">Nevolejte [metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody `ExecuteApplication` metodu aktivace manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="7d5aa-137">Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7d5aa-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d5aa-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d5aa-138">Requirements</span></span>  
 <span data-ttu-id="7d5aa-139">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d5aa-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d5aa-140">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d5aa-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d5aa-141">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d5aa-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d5aa-142">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d5aa-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d5aa-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d5aa-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="7d5aa-144">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d5aa-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="7d5aa-145">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="7d5aa-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="7d5aa-146">Návod: Stahování sestavení na vyžádání rozhraním API pro nasazení ClickOnce pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="7d5aa-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
