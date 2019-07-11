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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aabc5783e66893d13aed60e04d7ea5f6547c68
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773566"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="3bb3f-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="3bb3f-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="3bb3f-103">Získá identitu sestavení, vytvoření vazby mezi daty pro sestavení v zadané cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bb3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bb3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bb3f-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="3bb3f-106">[in] Cesta k souboru, který má být vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3bb3f-107">[in] Hodnota [eclrassemblyidentityflags –](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) výčet, který určuje typ identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-107">[in] A value of the [ECLRAssemblyIdentityFlags](../../../../docs/framework/unmanaged-api/hosting/eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="3bb3f-108">K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-108">Provided for future extensibility.</span></span> <span data-ttu-id="3bb3f-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje modul CLR (CLR) verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="3bb3f-110">[out] Vyrovnávací paměť obsahující data identit neprůhledné sestavení.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="3bb3f-111">[out v] Ukazatel na velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bb3f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3bb3f-112">Return Value</span></span>  
  
|<span data-ttu-id="3bb3f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bb3f-113">HRESULT</span></span>|<span data-ttu-id="3bb3f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3bb3f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bb3f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bb3f-115">S_OK</span></span>|<span data-ttu-id="3bb3f-116">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="3bb3f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3bb3f-117">E_INVALIDARG</span></span>|<span data-ttu-id="3bb3f-118">Zadané `pwzFilePath` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="3bb3f-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3bb3f-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3bb3f-120">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="3bb3f-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bb3f-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bb3f-122">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bb3f-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bb3f-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bb3f-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-124">The call timed out.</span></span>|  
|<span data-ttu-id="3bb3f-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bb3f-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bb3f-126">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bb3f-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bb3f-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bb3f-128">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bb3f-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bb3f-129">E_FAIL</span></span>|<span data-ttu-id="3bb3f-130">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bb3f-131">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bb3f-132">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bb3f-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bb3f-133">Remarks</span></span>  
 <span data-ttu-id="3bb3f-134">`GetBindingIdentityFromFile` je obvykle volána dvakrát.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="3bb3f-135">První volání je zadán pro hodnotu null `pwzBuffer`, a metoda vrátí odpovídající velikost v `pcchBufferSize`.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="3bb3f-136">Druhém volání je zadán správně přidělené vyrovnávací paměti a vrátí metodu s daty skutečné velikosti paměti po dokončení.</span><span class="sxs-lookup"><span data-stu-id="3bb3f-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bb3f-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bb3f-137">Requirements</span></span>  
 <span data-ttu-id="3bb3f-138">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bb3f-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bb3f-139">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bb3f-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bb3f-140">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bb3f-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bb3f-141">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bb3f-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb3f-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bb3f-142">See also</span></span>

- [<span data-ttu-id="3bb3f-143">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bb3f-143">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3bb3f-144">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bb3f-144">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3bb3f-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bb3f-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
