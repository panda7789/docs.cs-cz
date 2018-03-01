---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5456d2747bb9c55d73fcc377036f5df1e8b10db0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="0a3fd-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="0a3fd-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="0a3fd-103">Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a3fd-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a3fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a3fd-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="0a3fd-106">[v] Cesta k souboru, který se vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0a3fd-107">[v] Hodnota [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) výčtu, která určuje typ identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="0a3fd-108">K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-108">Provided for future extensibility.</span></span> <span data-ttu-id="0a3fd-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje modul CLR (CLR) verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="0a3fd-110">[out] Vyrovnávací paměť obsahující data identit neprůhledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="0a3fd-111">[ve out] Ukazatel na velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a3fd-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0a3fd-112">Return Value</span></span>  
  
|<span data-ttu-id="0a3fd-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a3fd-113">HRESULT</span></span>|<span data-ttu-id="0a3fd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0a3fd-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a3fd-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a3fd-115">S_OK</span></span>|<span data-ttu-id="0a3fd-116">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="0a3fd-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a3fd-117">E_INVALIDARG</span></span>|<span data-ttu-id="0a3fd-118">Zadaných `pwzFilePath` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="0a3fd-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="0a3fd-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="0a3fd-120">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="0a3fd-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a3fd-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a3fd-122">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a3fd-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a3fd-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a3fd-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-124">The call timed out.</span></span>|  
|<span data-ttu-id="0a3fd-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a3fd-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a3fd-126">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a3fd-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a3fd-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a3fd-128">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a3fd-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a3fd-129">E_FAIL</span></span>|<span data-ttu-id="0a3fd-130">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a3fd-131">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a3fd-132">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a3fd-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a3fd-133">Remarks</span></span>  
 <span data-ttu-id="0a3fd-134">`GetBindingIdentityFromFile`obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="0a3fd-135">První volání poskytuje hodnotu null pro `pwzBuffer`, a vrátí metoda odpovídající velikost v `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="0a3fd-136">Druhé volání poskytuje správně přidělené vyrovnávací paměti, a vrátí metodu s skutečné vyrovnávací paměť dat po dokončení.</span><span class="sxs-lookup"><span data-stu-id="0a3fd-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a3fd-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a3fd-137">Requirements</span></span>  
 <span data-ttu-id="0a3fd-138">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a3fd-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a3fd-139">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a3fd-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a3fd-140">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a3fd-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a3fd-141">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a3fd-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3fd-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a3fd-142">See Also</span></span>  
 [<span data-ttu-id="0a3fd-143">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a3fd-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="0a3fd-144">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a3fd-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="0a3fd-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a3fd-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
