---
title: "ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51775f52e34f35d8ef9f3a8533363be73e9bd7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="52da7-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="52da7-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="52da7-103">Změní zásadu vazby pro zadaného sestavení a vytvoří se nová verze zásad.</span><span class="sxs-lookup"><span data-stu-id="52da7-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52da7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52da7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="52da7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52da7-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="52da7-106">[v] Identita sestavení, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="52da7-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="52da7-107">[v] Novou identitu upravené sestavení.</span><span class="sxs-lookup"><span data-stu-id="52da7-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="52da7-108">[v] Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="52da7-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="52da7-109">[v] Velikost vazby zásady, které mají být nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="52da7-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="52da7-110">[v] Logická nebo kombinace [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) hodnoty, indikujících řízení přesměrování.</span><span class="sxs-lookup"><span data-stu-id="52da7-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="52da7-111">[out] Ukazatel na vyrovnávací paměť, která obsahuje nové zásady data vazby.</span><span class="sxs-lookup"><span data-stu-id="52da7-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="52da7-112">[ve out] Ukazatel na velikost vyrovnávací paměť nového zásad vazby.</span><span class="sxs-lookup"><span data-stu-id="52da7-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52da7-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="52da7-113">Return Value</span></span>  
  
|<span data-ttu-id="52da7-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52da7-114">HRESULT</span></span>|<span data-ttu-id="52da7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="52da7-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="52da7-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="52da7-116">S_OK</span></span>|<span data-ttu-id="52da7-117">Zásady byl úspěšně upraven.</span><span class="sxs-lookup"><span data-stu-id="52da7-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="52da7-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="52da7-118">E_INVALIDARG</span></span>|<span data-ttu-id="52da7-119">`pwzSourceAssemblyIdentity`nebo `pwzTargetAssemblyIdentity` byl odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="52da7-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="52da7-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="52da7-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="52da7-121">`pbNewApplicationPolicy`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="52da7-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="52da7-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="52da7-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="52da7-123">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="52da7-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="52da7-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="52da7-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="52da7-125">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="52da7-125">The call timed out.</span></span>|  
|<span data-ttu-id="52da7-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="52da7-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="52da7-127">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="52da7-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="52da7-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="52da7-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="52da7-129">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="52da7-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="52da7-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="52da7-130">E_FAIL</span></span>|<span data-ttu-id="52da7-131">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="52da7-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="52da7-132">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="52da7-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="52da7-133">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="52da7-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52da7-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52da7-134">Remarks</span></span>  
 <span data-ttu-id="52da7-135">`ModifyApplicationPolicy` Nelze volat metodu dvakrát.</span><span class="sxs-lookup"><span data-stu-id="52da7-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="52da7-136">Prvním volání musí zadat hodnotu null pro `pbNewApplicationPolicy` parametr.</span><span class="sxs-lookup"><span data-stu-id="52da7-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="52da7-137">Toto volání se vrátí hodnotou potřebné pro `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="52da7-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="52da7-138">Druhé volání musí zadat tuto hodnotu pro `pcbNewAppPolicySize`a přejděte do vyrovnávací paměti této velikosti pro `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="52da7-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52da7-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52da7-139">Requirements</span></span>  
 <span data-ttu-id="52da7-140">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52da7-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52da7-141">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52da7-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52da7-142">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52da7-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52da7-143">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52da7-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52da7-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="52da7-144">See Also</span></span>  
 [<span data-ttu-id="52da7-145">Iclrhostbindingpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52da7-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
