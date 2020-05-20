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
ms.openlocfilehash: 5b537d59014afa783d3f8c5046cc02dad7ea7740
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615992"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="8c8fe-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="8c8fe-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>
<span data-ttu-id="8c8fe-103">Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-103">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c8fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c8fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c8fe-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="8c8fe-106">pro Cesta k souboru, který má být vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-106">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8c8fe-107">pro Hodnota výčtu [ECLRAssemblyIdentityFlags –](eclrassemblyidentityflags-enumeration.md) , která označuje typ identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-107">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="8c8fe-108">K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-108">Provided for future extensibility.</span></span> <span data-ttu-id="8c8fe-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, kterou podporuje modul CLR (Common Language Runtime) verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8c8fe-110">mimo Vyrovnávací paměť obsahující data identity neprůhledných sestavení</span><span class="sxs-lookup"><span data-stu-id="8c8fe-110">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8c8fe-111">[in, out] Ukazatel na velikost `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8c8fe-111">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c8fe-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8c8fe-112">Return Value</span></span>  
  
|<span data-ttu-id="8c8fe-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c8fe-113">HRESULT</span></span>|<span data-ttu-id="8c8fe-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c8fe-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c8fe-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c8fe-115">S_OK</span></span>|<span data-ttu-id="8c8fe-116">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="8c8fe-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8c8fe-117">E_INVALIDARG</span></span>|<span data-ttu-id="8c8fe-118">Zadaná hodnota `pwzFilePath` je null.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-118">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="8c8fe-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8c8fe-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8c8fe-120">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-120">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="8c8fe-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c8fe-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c8fe-122">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c8fe-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c8fe-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c8fe-124">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-124">The call timed out.</span></span>|  
|<span data-ttu-id="8c8fe-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c8fe-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c8fe-126">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c8fe-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c8fe-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c8fe-128">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c8fe-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c8fe-129">E_FAIL</span></span>|<span data-ttu-id="8c8fe-130">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c8fe-131">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c8fe-132">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c8fe-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c8fe-133">Remarks</span></span>  
 <span data-ttu-id="8c8fe-134">`GetBindingIdentityFromFile`se obvykle nazývá dvakrát.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-134">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="8c8fe-135">První volání dodá hodnotu null pro `pwzBuffer` a metoda vrátí odpovídající velikost v `pcchBufferSize` .</span><span class="sxs-lookup"><span data-stu-id="8c8fe-135">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="8c8fe-136">Druhé volání dodá vhodně přidělenou vyrovnávací paměť a metoda se vrátí se skutečnými daty vyrovnávací paměti po dokončení.</span><span class="sxs-lookup"><span data-stu-id="8c8fe-136">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c8fe-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c8fe-137">Requirements</span></span>  
 <span data-ttu-id="8c8fe-138">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c8fe-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c8fe-139">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c8fe-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c8fe-140">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c8fe-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c8fe-141">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c8fe-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c8fe-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c8fe-142">See also</span></span>

- [<span data-ttu-id="8c8fe-143">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c8fe-143">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8c8fe-144">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c8fe-144">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8c8fe-145">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c8fe-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
