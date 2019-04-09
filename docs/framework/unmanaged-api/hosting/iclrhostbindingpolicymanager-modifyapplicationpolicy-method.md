---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07a4998f86958e21fffc8ba8657ec9f2a170f43e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112434"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="8504e-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="8504e-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="8504e-103">Změní zásady vazeb pro zadané sestavení a vytvoří se nová verze zásad.</span><span class="sxs-lookup"><span data-stu-id="8504e-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8504e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8504e-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8504e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8504e-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="8504e-106">[in] Identita sestavení změnit.</span><span class="sxs-lookup"><span data-stu-id="8504e-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="8504e-107">[in] Nové identity upravené sestavení.</span><span class="sxs-lookup"><span data-stu-id="8504e-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="8504e-108">[in] Ukazatel do vyrovnávací paměti, která obsahuje data zásad vazby pro sestavení, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="8504e-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="8504e-109">[in] Velikost zásady vazeb, které mají být nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="8504e-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="8504e-110">[in] Logický OR kombinaci [ehostbindingpolicymodifyflags –](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) hodnoty určující kontrolu nad přesměrování.</span><span class="sxs-lookup"><span data-stu-id="8504e-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="8504e-111">[out] Ukazatel do vyrovnávací paměti, který obsahuje data nové zásady vazby.</span><span class="sxs-lookup"><span data-stu-id="8504e-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="8504e-112">[out v] Ukazatel na velikost vyrovnávací paměť nového zásady vazby.</span><span class="sxs-lookup"><span data-stu-id="8504e-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8504e-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8504e-113">Return Value</span></span>  
  
|<span data-ttu-id="8504e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8504e-114">HRESULT</span></span>|<span data-ttu-id="8504e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="8504e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8504e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="8504e-116">S_OK</span></span>|<span data-ttu-id="8504e-117">Tyto zásady se úspěšně změnily.</span><span class="sxs-lookup"><span data-stu-id="8504e-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="8504e-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8504e-118">E_INVALIDARG</span></span>|`pwzSourceAssemblyIdentity` <span data-ttu-id="8504e-119">nebo `pwzTargetAssemblyIdentity` byl odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8504e-119">or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="8504e-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8504e-120">ERROR_INSUFFICIENT_BUFFER</span></span>|`pbNewApplicationPolicy` <span data-ttu-id="8504e-121">je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="8504e-121">is too small.</span></span>|  
|<span data-ttu-id="8504e-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8504e-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8504e-123">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8504e-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8504e-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8504e-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8504e-125">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8504e-125">The call timed out.</span></span>|  
|<span data-ttu-id="8504e-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8504e-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8504e-127">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="8504e-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8504e-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8504e-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8504e-129">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="8504e-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8504e-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8504e-130">E_FAIL</span></span>|<span data-ttu-id="8504e-131">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="8504e-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8504e-132">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="8504e-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8504e-133">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8504e-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8504e-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8504e-134">Remarks</span></span>  
 <span data-ttu-id="8504e-135">`ModifyApplicationPolicy` Metodu lze volat dvakrát.</span><span class="sxs-lookup"><span data-stu-id="8504e-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="8504e-136">První volání by mělo nabízet pro hodnotu null `pbNewApplicationPolicy` parametru.</span><span class="sxs-lookup"><span data-stu-id="8504e-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="8504e-137">Toto volání vrátí hodnotou nezbytné pro `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="8504e-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="8504e-138">Druhé volání by mělo nabízet tuto hodnotu pro `pcbNewAppPolicySize`a přejděte do vyrovnávací paměti, že velikosti pro `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="8504e-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8504e-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8504e-139">Requirements</span></span>  
 <span data-ttu-id="8504e-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8504e-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8504e-141">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8504e-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8504e-142">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8504e-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8504e-143">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8504e-143">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8504e-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8504e-144">See also</span></span>

- [<span data-ttu-id="8504e-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8504e-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
