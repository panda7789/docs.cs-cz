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
ms.openlocfilehash: e32714bba2403752f1ac2551ab182f2655f1fa75
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703853"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="011cb-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="011cb-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="011cb-103">Upraví zásadu vazby pro zadané sestavení a vytvoří novou verzi zásad.</span><span class="sxs-lookup"><span data-stu-id="011cb-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="011cb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="011cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="011cb-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="011cb-106">pro Identita sestavení, které má být upraveno.</span><span class="sxs-lookup"><span data-stu-id="011cb-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="011cb-107">pro Nová identita upraveného sestavení.</span><span class="sxs-lookup"><span data-stu-id="011cb-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="011cb-108">pro Ukazatel na vyrovnávací paměť, která obsahuje data zásad vazby pro sestavení, které chcete upravit.</span><span class="sxs-lookup"><span data-stu-id="011cb-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="011cb-109">pro Velikost zásady vazby, která má být nahrazena.</span><span class="sxs-lookup"><span data-stu-id="011cb-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="011cb-110">pro Logická nebo kombinovaná hodnota [EHostBindingPolicyModifyFlags –](ehostbindingpolicymodifyflags-enumeration.md) , která označuje řízení přesměrování.</span><span class="sxs-lookup"><span data-stu-id="011cb-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="011cb-111">mimo Ukazatel na vyrovnávací paměť, která obsahuje nová data zásad vazby.</span><span class="sxs-lookup"><span data-stu-id="011cb-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="011cb-112">[in, out] Ukazatel na velikost nové vyrovnávací paměti zásad vazby.</span><span class="sxs-lookup"><span data-stu-id="011cb-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="011cb-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="011cb-113">Return Value</span></span>  
  
|<span data-ttu-id="011cb-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="011cb-114">HRESULT</span></span>|<span data-ttu-id="011cb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="011cb-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="011cb-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="011cb-116">S_OK</span></span>|<span data-ttu-id="011cb-117">Zásady se úspěšně změnily.</span><span class="sxs-lookup"><span data-stu-id="011cb-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="011cb-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="011cb-118">E_INVALIDARG</span></span>|<span data-ttu-id="011cb-119">`pwzSourceAssemblyIdentity`nebo `pwzTargetAssemblyIdentity` se jednalo o odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="011cb-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="011cb-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="011cb-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="011cb-121">`pbNewApplicationPolicy`je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="011cb-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="011cb-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="011cb-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="011cb-123">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="011cb-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="011cb-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="011cb-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="011cb-125">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="011cb-125">The call timed out.</span></span>|  
|<span data-ttu-id="011cb-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="011cb-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="011cb-127">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="011cb-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="011cb-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="011cb-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="011cb-129">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="011cb-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="011cb-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="011cb-130">E_FAIL</span></span>|<span data-ttu-id="011cb-131">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="011cb-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="011cb-132">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="011cb-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="011cb-133">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="011cb-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="011cb-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="011cb-134">Remarks</span></span>  
 <span data-ttu-id="011cb-135">`ModifyApplicationPolicy`Metodu lze volat dvakrát.</span><span class="sxs-lookup"><span data-stu-id="011cb-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="011cb-136">První volání by mělo pro parametr dodat hodnotu null `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="011cb-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="011cb-137">Toto volání se vrátí s potřebnou hodnotou pro `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="011cb-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="011cb-138">Druhé volání by mělo uvést tuto hodnotu pro `pcbNewAppPolicySize` a odkazovat na vyrovnávací paměť této velikosti pro `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="011cb-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="011cb-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="011cb-139">Requirements</span></span>  
 <span data-ttu-id="011cb-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="011cb-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="011cb-141">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="011cb-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="011cb-142">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="011cb-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="011cb-143">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="011cb-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011cb-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="011cb-144">See also</span></span>

- [<span data-ttu-id="011cb-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="011cb-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
