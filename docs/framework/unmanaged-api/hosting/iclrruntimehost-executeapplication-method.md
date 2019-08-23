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
ms.openlocfilehash: 38938de335e5f0d7cb8051554c400f16df012362
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965360"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="d5100-102">ICLRRuntimeHost::ExecuteApplication – metoda</span><span class="sxs-lookup"><span data-stu-id="d5100-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="d5100-103">Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.</span><span class="sxs-lookup"><span data-stu-id="d5100-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="d5100-104">Další informace o těchto scénářích najdete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="d5100-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5100-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5100-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d5100-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5100-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="d5100-107">pro Úplný název aplikace definovaný pro <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="d5100-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="d5100-108">pro Počet řetězců obsažených v `ppwzManifestPaths` poli.</span><span class="sxs-lookup"><span data-stu-id="d5100-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="d5100-109">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d5100-109">[in] Optional.</span></span> <span data-ttu-id="d5100-110">Pole řetězců, které obsahuje cesty manifestu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d5100-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="d5100-111">pro Počet řetězců obsažených v `ppwzActivationData` poli.</span><span class="sxs-lookup"><span data-stu-id="d5100-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="d5100-112">pro Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d5100-112">[in] Optional.</span></span> <span data-ttu-id="d5100-113">Pole řetězců, které obsahuje aktivační data aplikace, jako je například část řetězce dotazu adresy URL pro aplikace nasazené na webu.</span><span class="sxs-lookup"><span data-stu-id="d5100-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="d5100-114">mimo Hodnota vrácená vstupním bodem aplikace</span><span class="sxs-lookup"><span data-stu-id="d5100-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5100-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d5100-115">Return Value</span></span>  
  
|<span data-ttu-id="d5100-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5100-116">HRESULT</span></span>|<span data-ttu-id="d5100-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d5100-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5100-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5100-118">S_OK</span></span>|<span data-ttu-id="d5100-119">`ExecuteApplication`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d5100-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="d5100-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5100-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5100-121">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d5100-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d5100-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5100-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5100-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d5100-123">The call timed out.</span></span>|  
|<span data-ttu-id="d5100-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5100-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5100-125">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d5100-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5100-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5100-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5100-127">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d5100-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5100-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5100-128">E_FAIL</span></span>|<span data-ttu-id="d5100-129">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d5100-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5100-130">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d5100-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5100-131">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d5100-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5100-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5100-132">Remarks</span></span>  
 <span data-ttu-id="d5100-133">`ExecuteApplication`slouží k aktivaci aplikací ClickOnce v nově vytvořené doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5100-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="d5100-134">`pReturnValue` Výstupní parametr je nastaven na hodnotu vrácenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="d5100-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="d5100-135">Pokud zadáte hodnotu null pro `pReturnValue`, `ExecuteApplication` neselže, ale nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5100-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d5100-136">Nevolejte metodu [počáteční metody](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním `ExecuteApplication` metody pro aktivaci aplikace založené na manifestu.</span><span class="sxs-lookup"><span data-stu-id="d5100-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="d5100-137">`ExecuteApplication` Pokud je `Start` metoda volána jako první, volání metody se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="d5100-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5100-138">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5100-138">Requirements</span></span>  
 <span data-ttu-id="d5100-139">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5100-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5100-140">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5100-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5100-141">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5100-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5100-142">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5100-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5100-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5100-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="d5100-144">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5100-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="d5100-145">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="d5100-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="d5100-146">Návod: Stahování sestavení na vyžádání rozhraním API pro nasazení ClickOnce pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="d5100-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
