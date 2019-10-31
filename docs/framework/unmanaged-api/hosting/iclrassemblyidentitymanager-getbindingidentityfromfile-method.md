---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 19d6a76d62680be91a7b9721912ca528edde7511
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126758"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="d2db3-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d2db3-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="d2db3-103">Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="d2db3-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2db3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2db3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2db3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2db3-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d2db3-106">pro Cesta k souboru, který má být vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="d2db3-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d2db3-107">pro Hodnota výčtu [ECLRAssemblyIdentityFlags –](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) , která označuje typ identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2db3-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="d2db3-108">K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d2db3-108">Provided for future extensibility.</span></span> <span data-ttu-id="d2db3-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou podporuje modul CLR (Common Language Runtime) verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="d2db3-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="d2db3-110">mimo Vyrovnávací paměť obsahující data identity neprůhledných sestavení</span><span class="sxs-lookup"><span data-stu-id="d2db3-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="d2db3-111">[in, out] Ukazatel na velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="d2db3-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2db3-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d2db3-112">Return Value</span></span>  
  
|<span data-ttu-id="d2db3-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2db3-113">HRESULT</span></span>|<span data-ttu-id="d2db3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d2db3-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2db3-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2db3-115">S_OK</span></span>|<span data-ttu-id="d2db3-116">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d2db3-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="d2db3-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d2db3-117">E_INVALIDARG</span></span>|<span data-ttu-id="d2db3-118">Poskytnutý `pwzFilePath` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d2db3-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="d2db3-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d2db3-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d2db3-120">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="d2db3-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="d2db3-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d2db3-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d2db3-122">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d2db3-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d2db3-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d2db3-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d2db3-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d2db3-124">The call timed out.</span></span>|  
|<span data-ttu-id="d2db3-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d2db3-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d2db3-126">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d2db3-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d2db3-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d2db3-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d2db3-128">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d2db3-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d2db3-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d2db3-129">E_FAIL</span></span>|<span data-ttu-id="d2db3-130">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d2db3-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d2db3-131">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d2db3-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d2db3-132">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d2db3-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2db3-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2db3-133">Remarks</span></span>  
 <span data-ttu-id="d2db3-134">`GetBindingIdentityFromFile` se obvykle volá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="d2db3-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="d2db3-135">První volání dodá hodnotu null pro `pwzBuffer`a metoda vrátí odpovídající velikost v `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="d2db3-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="d2db3-136">Druhé volání dodá vhodně přidělenou vyrovnávací paměť a metoda se vrátí se skutečnými daty vyrovnávací paměti po dokončení.</span><span class="sxs-lookup"><span data-stu-id="d2db3-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2db3-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2db3-137">Requirements</span></span>  
 <span data-ttu-id="d2db3-138">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2db3-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2db3-139">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2db3-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2db3-140">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2db3-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2db3-141">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2db3-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2db3-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2db3-142">See also</span></span>

- [<span data-ttu-id="d2db3-143">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2db3-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d2db3-144">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2db3-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d2db3-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2db3-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
