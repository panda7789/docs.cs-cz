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
ms.openlocfilehash: 9e37d56a321e6529812045e37c4f1929818b38a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433604"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="93090-102">ICLRHostBindingPolicyManager::EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="93090-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="93090-103">Vyhodnotí zásady vazby jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="93090-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93090-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93090-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="93090-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93090-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="93090-106">[v] Odkaz na sestavení před vyhodnocení zásad.</span><span class="sxs-lookup"><span data-stu-id="93090-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="93090-107">[v] Ukazatel na vyrovnávací paměť, která obsahuje data zásad.</span><span class="sxs-lookup"><span data-stu-id="93090-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="93090-108">[v] Velikost `pbApplicationPolicy` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="93090-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="93090-109">[out] Odkaz na sestavení po skončení testování nových dat zásad.</span><span class="sxs-lookup"><span data-stu-id="93090-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="93090-110">[ve out] Ukazatel na velikost vyrovnávací paměti identity odkaz na sestavení po skončení testování nových dat zásad.</span><span class="sxs-lookup"><span data-stu-id="93090-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="93090-111">[out] Ukazatel na logické nebo kombinaci [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hodnoty, která určuje, které zásady platí.</span><span class="sxs-lookup"><span data-stu-id="93090-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93090-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="93090-112">Return Value</span></span>  
  
|<span data-ttu-id="93090-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93090-113">HRESULT</span></span>|<span data-ttu-id="93090-114">Popis</span><span class="sxs-lookup"><span data-stu-id="93090-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93090-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="93090-115">S_OK</span></span>|<span data-ttu-id="93090-116">Vyhodnocení byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="93090-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="93090-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="93090-117">E_INVALIDARG</span></span>|<span data-ttu-id="93090-118">Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy` se odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="93090-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="93090-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="93090-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="93090-120">`cbAppPolicySize` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="93090-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="93090-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93090-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93090-122">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="93090-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93090-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93090-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93090-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="93090-124">The call timed out.</span></span>|  
|<span data-ttu-id="93090-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93090-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93090-126">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="93090-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93090-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93090-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93090-128">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="93090-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93090-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93090-129">E_FAIL</span></span>|<span data-ttu-id="93090-130">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="93090-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93090-131">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="93090-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93090-132">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="93090-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93090-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93090-133">Remarks</span></span>  
 <span data-ttu-id="93090-134">`EvaluatePolicy` Metoda umožňuje hostitele k ovlivnění vazby zásady zachování konkrétního hostitele sestavení požadavků na správu verzí.</span><span class="sxs-lookup"><span data-stu-id="93090-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="93090-135">Modul zásad, samotné zůstane uvnitř modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="93090-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93090-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="93090-136">Requirements</span></span>  
 <span data-ttu-id="93090-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93090-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93090-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93090-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93090-139">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93090-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93090-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93090-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93090-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="93090-141">See Also</span></span>  
 [<span data-ttu-id="93090-142">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="93090-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
