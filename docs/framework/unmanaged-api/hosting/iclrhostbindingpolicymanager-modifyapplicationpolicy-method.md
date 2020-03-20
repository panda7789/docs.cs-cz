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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178105"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="befd0-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="befd0-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="befd0-103">Upraví zásady vazby pro zadané sestavení a vytvoří novou verzi zásady.</span><span class="sxs-lookup"><span data-stu-id="befd0-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="befd0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="befd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="befd0-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="befd0-106">[v] Identita sestavení upravit.</span><span class="sxs-lookup"><span data-stu-id="befd0-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="befd0-107">[v] Nová identita upravenésestavení.</span><span class="sxs-lookup"><span data-stu-id="befd0-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="befd0-108">[v] Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení upravit.</span><span class="sxs-lookup"><span data-stu-id="befd0-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="befd0-109">[v] Velikost zásady vazby, které mají být nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="befd0-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="befd0-110">[v] Logická kombinace nebo hodnot [EHostBindingPolicyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) označující řízení přesměrování.</span><span class="sxs-lookup"><span data-stu-id="befd0-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="befd0-111">[out] Ukazatel na vyrovnávací paměť, která obsahuje nová data zásad vazby.</span><span class="sxs-lookup"><span data-stu-id="befd0-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="befd0-112">[dovnitř, ven] Ukazatel na velikost vyrovnávací paměti zásad y nové vazby.</span><span class="sxs-lookup"><span data-stu-id="befd0-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="befd0-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="befd0-113">Return Value</span></span>  
  
|<span data-ttu-id="befd0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="befd0-114">HRESULT</span></span>|<span data-ttu-id="befd0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="befd0-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="befd0-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="befd0-116">S_OK</span></span>|<span data-ttu-id="befd0-117">Zásada byla úspěšně změněna.</span><span class="sxs-lookup"><span data-stu-id="befd0-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="befd0-118">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="befd0-118">E_INVALIDARG</span></span>|<span data-ttu-id="befd0-119">`pwzSourceAssemblyIdentity`nebo `pwzTargetAssemblyIdentity` byl nulový odkaz.</span><span class="sxs-lookup"><span data-stu-id="befd0-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="befd0-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="befd0-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="befd0-121">`pbNewApplicationPolicy`je příliš malý.</span><span class="sxs-lookup"><span data-stu-id="befd0-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="befd0-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="befd0-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="befd0-123">Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="befd0-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="befd0-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="befd0-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="befd0-125">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="befd0-125">The call timed out.</span></span>|  
|<span data-ttu-id="befd0-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="befd0-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="befd0-127">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="befd0-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="befd0-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="befd0-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="befd0-129">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="befd0-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="befd0-130">E_fail</span><span class="sxs-lookup"><span data-stu-id="befd0-130">E_FAIL</span></span>|<span data-ttu-id="befd0-131">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="befd0-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="befd0-132">Po metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="befd0-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="befd0-133">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="befd0-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="befd0-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="befd0-134">Remarks</span></span>  
 <span data-ttu-id="befd0-135">Metoda `ModifyApplicationPolicy` může být volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="befd0-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="befd0-136">První volání by mělo poskytnout `pbNewApplicationPolicy` hodnotu null pro parametr.</span><span class="sxs-lookup"><span data-stu-id="befd0-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="befd0-137">Toto volání se vrátí `pcbNewAppPolicySize`s potřebnou hodnotou pro .</span><span class="sxs-lookup"><span data-stu-id="befd0-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="befd0-138">Druhé volání by mělo `pcbNewAppPolicySize`zadat tuto hodnotu pro a `pbNewApplicationPolicy`přejděte na vyrovnávací paměť této velikosti pro .</span><span class="sxs-lookup"><span data-stu-id="befd0-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="befd0-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="befd0-139">Requirements</span></span>  
 <span data-ttu-id="befd0-140">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="befd0-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="befd0-141">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="befd0-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="befd0-142">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="befd0-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="befd0-143">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="befd0-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befd0-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="befd0-144">See also</span></span>

- [<span data-ttu-id="befd0-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="befd0-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
