---
title: ICLRHostBindingPolicyManager::EvaluatePolicy – metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 970e57e3caee7631c8e85aef428df52ec293b9cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648807"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="1015e-102">ICLRHostBindingPolicyManager::EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="1015e-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="1015e-103">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="1015e-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1015e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1015e-104">Syntax</span></span>  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1015e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1015e-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="1015e-106">[in] Odkaz na sestavení před vyhodnocení zásad.</span><span class="sxs-lookup"><span data-stu-id="1015e-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="1015e-107">[in] Ukazatel do vyrovnávací paměti, která obsahuje data zásad.</span><span class="sxs-lookup"><span data-stu-id="1015e-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="1015e-108">[in] Velikost `pbApplicationPolicy` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1015e-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="1015e-109">[out] Odkaz na sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="1015e-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="1015e-110">[out v] Ukazatel na velikost vyrovnávací paměti identity odkaz sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="1015e-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="1015e-111">[out] Ukazatel na logický OR kombinaci [ebindpolicylevels –](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hodnoty určující, které zásady byly použity.</span><span class="sxs-lookup"><span data-stu-id="1015e-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1015e-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1015e-112">Return Value</span></span>  
  
|<span data-ttu-id="1015e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1015e-113">HRESULT</span></span>|<span data-ttu-id="1015e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1015e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1015e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1015e-115">S_OK</span></span>|<span data-ttu-id="1015e-116">Vyhodnocení bylo úspěšně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="1015e-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="1015e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1015e-117">E_INVALIDARG</span></span>|<span data-ttu-id="1015e-118">Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy` je nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="1015e-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="1015e-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1015e-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1015e-120">`cbAppPolicySize` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="1015e-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="1015e-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1015e-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1015e-122">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1015e-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1015e-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1015e-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1015e-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1015e-124">The call timed out.</span></span>|  
|<span data-ttu-id="1015e-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1015e-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1015e-126">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="1015e-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1015e-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1015e-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1015e-128">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="1015e-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1015e-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1015e-129">E_FAIL</span></span>|<span data-ttu-id="1015e-130">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="1015e-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1015e-131">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1015e-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1015e-132">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1015e-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1015e-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1015e-133">Remarks</span></span>  
 <span data-ttu-id="1015e-134">`EvaluatePolicy` Metoda umožňuje hostitele tak, aby ovlivňovala zásady vazby udržovat sestavení hostitele specifické požadavky na správu verzí.</span><span class="sxs-lookup"><span data-stu-id="1015e-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="1015e-135">Samotný modul zásad zůstane uvnitř modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1015e-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1015e-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1015e-136">Requirements</span></span>  
 <span data-ttu-id="1015e-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1015e-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1015e-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1015e-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1015e-139">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1015e-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1015e-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1015e-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1015e-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1015e-141">See also</span></span>
- [<span data-ttu-id="1015e-142">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1015e-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
