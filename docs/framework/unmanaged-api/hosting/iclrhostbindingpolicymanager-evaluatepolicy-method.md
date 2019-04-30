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
ms.openlocfilehash: ad7856a9376880f867e35f1e63bc2cac1ca216fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794482"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="c4dbe-102">ICLRHostBindingPolicyManager::EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="c4dbe-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="c4dbe-103">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4dbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4dbe-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c4dbe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4dbe-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="c4dbe-106">[in] Odkaz na sestavení před vyhodnocení zásad.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="c4dbe-107">[in] Ukazatel do vyrovnávací paměti, která obsahuje data zásad.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="c4dbe-108">[in] Velikost `pbApplicationPolicy` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="c4dbe-109">[out] Odkaz na sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="c4dbe-110">[out v] Ukazatel na velikost vyrovnávací paměti identity odkaz sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="c4dbe-111">[out] Ukazatel na logický OR kombinaci [ebindpolicylevels –](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hodnoty určující, které zásady byly použity.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4dbe-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4dbe-112">Return Value</span></span>  
  
|<span data-ttu-id="c4dbe-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4dbe-113">HRESULT</span></span>|<span data-ttu-id="c4dbe-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c4dbe-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4dbe-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4dbe-115">S_OK</span></span>|<span data-ttu-id="c4dbe-116">Vyhodnocení bylo úspěšně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="c4dbe-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4dbe-117">E_INVALIDARG</span></span>|<span data-ttu-id="c4dbe-118">Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy` je nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="c4dbe-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c4dbe-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c4dbe-120">`cbAppPolicySize` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="c4dbe-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4dbe-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4dbe-122">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4dbe-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4dbe-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4dbe-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-124">The call timed out.</span></span>|  
|<span data-ttu-id="c4dbe-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4dbe-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4dbe-126">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4dbe-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4dbe-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4dbe-128">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4dbe-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4dbe-129">E_FAIL</span></span>|<span data-ttu-id="c4dbe-130">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4dbe-131">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4dbe-132">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4dbe-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4dbe-133">Remarks</span></span>  
 <span data-ttu-id="c4dbe-134">`EvaluatePolicy` Metoda umožňuje hostitele tak, aby ovlivňovala zásady vazby udržovat sestavení hostitele specifické požadavky na správu verzí.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="c4dbe-135">Samotný modul zásad zůstane uvnitř modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c4dbe-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4dbe-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4dbe-136">Requirements</span></span>  
 <span data-ttu-id="c4dbe-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4dbe-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4dbe-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4dbe-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4dbe-139">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4dbe-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4dbe-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4dbe-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4dbe-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4dbe-141">See also</span></span>

- [<span data-ttu-id="c4dbe-142">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4dbe-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
