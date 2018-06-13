---
title: ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57cf4e9f79be8e705869cf986a586fcfb3359584
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435336"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="221e4-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="221e4-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="221e4-103">Získá data identit kanonický sestavení pro sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="221e4-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="221e4-104">Syntax</span></span>  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="221e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="221e4-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="221e4-106">[v] Sestavení datový proud, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="221e4-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="221e4-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="221e4-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="221e4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="221e4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="221e4-109">[out] Vyrovnávací paměť obsahující data identit neprůhledného sestavení.</span><span class="sxs-lookup"><span data-stu-id="221e4-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="221e4-110">[ve out] Velikost `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="221e4-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="221e4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="221e4-111">Return Value</span></span>  
  
|<span data-ttu-id="221e4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="221e4-112">HRESULT</span></span>|<span data-ttu-id="221e4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="221e4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="221e4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="221e4-114">S_OK</span></span>|<span data-ttu-id="221e4-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="221e4-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="221e4-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="221e4-116">E_INVALIDARG</span></span>|<span data-ttu-id="221e4-117">Zadaných `pStream` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="221e4-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="221e4-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="221e4-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="221e4-119">Velikost `pwzBuffer` je příliš malá.</span><span class="sxs-lookup"><span data-stu-id="221e4-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="221e4-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="221e4-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="221e4-121">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="221e4-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="221e4-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="221e4-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="221e4-123">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="221e4-123">The call timed out.</span></span>|  
|<span data-ttu-id="221e4-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="221e4-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="221e4-125">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="221e4-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="221e4-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="221e4-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="221e4-127">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="221e4-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="221e4-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="221e4-128">E_FAIL</span></span>|<span data-ttu-id="221e4-129">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="221e4-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="221e4-130">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="221e4-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="221e4-131">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="221e4-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="221e4-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="221e4-132">Requirements</span></span>  
 <span data-ttu-id="221e4-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="221e4-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="221e4-134">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="221e4-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="221e4-135">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="221e4-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="221e4-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="221e4-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221e4-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="221e4-137">See Also</span></span>  
 [<span data-ttu-id="221e4-138">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="221e4-138">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="221e4-139">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="221e4-139">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
