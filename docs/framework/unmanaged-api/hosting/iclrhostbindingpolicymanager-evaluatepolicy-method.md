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
ms.openlocfilehash: 7d23b2371e7cc3c9d1e91af061c19b4fb0dbc69e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779695"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="fe1a6-102">ICLRHostBindingPolicyManager::EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="fe1a6-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="fe1a6-103">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe1a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe1a6-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe1a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe1a6-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="fe1a6-106">[in] Odkaz na sestavení před vyhodnocení zásad.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="fe1a6-107">[in] Ukazatel do vyrovnávací paměti, která obsahuje data zásad.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="fe1a6-108">[in] Velikost `pbApplicationPolicy` vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="fe1a6-109">[out] Odkaz na sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="fe1a6-110">[out v] Ukazatel na velikost vyrovnávací paměti identity odkaz sestavení po skončení testování nová data zásad.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="fe1a6-111">[out] Ukazatel na logický OR kombinaci [ebindpolicylevels –](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) hodnoty určující, které zásady byly použity.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe1a6-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fe1a6-112">Return Value</span></span>  
  
|<span data-ttu-id="fe1a6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe1a6-113">HRESULT</span></span>|<span data-ttu-id="fe1a6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fe1a6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe1a6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe1a6-115">S_OK</span></span>|<span data-ttu-id="fe1a6-116">Vyhodnocení bylo úspěšně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="fe1a6-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fe1a6-117">E_INVALIDARG</span></span>|<span data-ttu-id="fe1a6-118">Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy` je nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="fe1a6-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fe1a6-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fe1a6-120">`cbAppPolicySize` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="fe1a6-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe1a6-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe1a6-122">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe1a6-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe1a6-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe1a6-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-124">The call timed out.</span></span>|  
|<span data-ttu-id="fe1a6-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe1a6-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe1a6-126">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe1a6-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe1a6-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe1a6-128">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe1a6-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe1a6-129">E_FAIL</span></span>|<span data-ttu-id="fe1a6-130">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe1a6-131">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe1a6-132">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe1a6-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe1a6-133">Remarks</span></span>  
 <span data-ttu-id="fe1a6-134">`EvaluatePolicy` Metoda umožňuje hostitele tak, aby ovlivňovala zásady vazby udržovat sestavení hostitele specifické požadavky na správu verzí.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="fe1a6-135">Samotný modul zásad zůstane uvnitř modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fe1a6-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe1a6-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe1a6-136">Requirements</span></span>  
 <span data-ttu-id="fe1a6-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe1a6-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe1a6-138">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe1a6-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe1a6-139">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe1a6-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe1a6-140">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe1a6-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1a6-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe1a6-141">See also</span></span>

- [<span data-ttu-id="fe1a6-142">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe1a6-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
