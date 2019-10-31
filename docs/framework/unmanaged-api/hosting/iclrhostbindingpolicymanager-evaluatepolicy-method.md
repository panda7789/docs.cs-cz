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
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141188"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="979e8-102">ICLRHostBindingPolicyManager::EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="979e8-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="979e8-103">Vyhodnotí zásady vytváření vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="979e8-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="979e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="979e8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="979e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="979e8-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="979e8-106">pro Odkaz na sestavení před vyhodnocením zásad.</span><span class="sxs-lookup"><span data-stu-id="979e8-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="979e8-107">pro Ukazatel na vyrovnávací paměť, která obsahuje data zásad.</span><span class="sxs-lookup"><span data-stu-id="979e8-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="979e8-108">pro Velikost vyrovnávací paměti `pbApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="979e8-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="979e8-109">mimo Odkaz na sestavení po vyhodnocení nových dat zásad</span><span class="sxs-lookup"><span data-stu-id="979e8-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="979e8-110">[in, out] Ukazatel na velikost vyrovnávací paměti odkazu identity sestavení po vyhodnocení nových dat zásad.</span><span class="sxs-lookup"><span data-stu-id="979e8-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="979e8-111">mimo Ukazatel na logickou nebo kombinaci hodnot [EBindPolicyLevels –](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) , které označují, které zásady byly aplikovány.</span><span class="sxs-lookup"><span data-stu-id="979e8-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="979e8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="979e8-112">Return Value</span></span>  
  
|<span data-ttu-id="979e8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="979e8-113">HRESULT</span></span>|<span data-ttu-id="979e8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="979e8-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="979e8-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="979e8-115">S_OK</span></span>|<span data-ttu-id="979e8-116">Vyhodnocení bylo úspěšně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="979e8-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="979e8-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="979e8-117">E_INVALIDARG</span></span>|<span data-ttu-id="979e8-118">Buď `pwzReferenceIdentity` nebo `pbApplicationPolicy`, je odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="979e8-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="979e8-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="979e8-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="979e8-120">`cbAppPolicySize` je příliš malý.</span><span class="sxs-lookup"><span data-stu-id="979e8-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="979e8-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="979e8-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="979e8-122">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="979e8-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="979e8-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="979e8-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="979e8-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="979e8-124">The call timed out.</span></span>|  
|<span data-ttu-id="979e8-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="979e8-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="979e8-126">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="979e8-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="979e8-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="979e8-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="979e8-128">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="979e8-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="979e8-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="979e8-129">E_FAIL</span></span>|<span data-ttu-id="979e8-130">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="979e8-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="979e8-131">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="979e8-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="979e8-132">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="979e8-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="979e8-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="979e8-133">Remarks</span></span>  
 <span data-ttu-id="979e8-134">Metoda `EvaluatePolicy` umožňuje hostiteli ovlivnit zásady vazeb pro zachování požadavků na správu verzí sestavení specifických pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="979e8-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="979e8-135">Samotný modul zásad zůstává v rámci CLR.</span><span class="sxs-lookup"><span data-stu-id="979e8-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="979e8-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="979e8-136">Requirements</span></span>  
 <span data-ttu-id="979e8-137">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="979e8-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="979e8-138">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="979e8-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="979e8-139">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="979e8-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="979e8-140">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="979e8-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979e8-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="979e8-141">See also</span></span>

- [<span data-ttu-id="979e8-142">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="979e8-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
