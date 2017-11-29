---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 140240f5f108cdd26cd0e813d7fe47f102a3b941
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="a747c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a747c-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="a747c-103">Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="a747c-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a747c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a747c-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a747c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a747c-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="a747c-106">[v] Cesta k souboru, který se vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="a747c-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a747c-107">[v] Hodnota [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) výčtu, která určuje typ identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="a747c-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="a747c-108">K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="a747c-108">Provided for future extensibility.</span></span> <span data-ttu-id="a747c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje modul CLR (CLR) verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="a747c-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a747c-110">[out] Vyrovnávací paměť obsahující data identit neprůhledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="a747c-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a747c-111">[ve out] Ukazatel na velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="a747c-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a747c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a747c-112">Return Value</span></span>  
  
|<span data-ttu-id="a747c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a747c-113">HRESULT</span></span>|<span data-ttu-id="a747c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a747c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a747c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a747c-115">S_OK</span></span>|<span data-ttu-id="a747c-116">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a747c-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="a747c-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a747c-117">E_INVALIDARG</span></span>|<span data-ttu-id="a747c-118">Zadaných `pwzFilePath` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a747c-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="a747c-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a747c-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a747c-120">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="a747c-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a747c-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a747c-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a747c-122">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a747c-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a747c-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a747c-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a747c-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a747c-124">The call timed out.</span></span>|  
|<span data-ttu-id="a747c-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a747c-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a747c-126">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a747c-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a747c-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a747c-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a747c-128">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a747c-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a747c-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a747c-129">E_FAIL</span></span>|<span data-ttu-id="a747c-130">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a747c-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a747c-131">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a747c-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a747c-132">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a747c-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a747c-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a747c-133">Remarks</span></span>  
 <span data-ttu-id="a747c-134">`GetBindingIdentityFromFile`obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="a747c-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="a747c-135">První volání poskytuje hodnotu null pro `pwzBuffer`, a vrátí metoda odpovídající velikost v `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="a747c-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="a747c-136">Druhé volání poskytuje správně přidělené vyrovnávací paměti, a vrátí metodu s skutečné vyrovnávací paměť dat po dokončení.</span><span class="sxs-lookup"><span data-stu-id="a747c-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a747c-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a747c-137">Requirements</span></span>  
 <span data-ttu-id="a747c-138">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a747c-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a747c-139">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a747c-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a747c-140">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a747c-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a747c-141">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a747c-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a747c-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="a747c-142">See Also</span></span>  
 [<span data-ttu-id="a747c-143">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a747c-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="a747c-144">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a747c-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="a747c-145">Iclrhostbindingpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a747c-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
