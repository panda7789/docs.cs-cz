---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abd80676fe459bd779d5fad4cf2e9c41e140741b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="230a0-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="230a0-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="230a0-103">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instanci, která obsahuje seznam sestavení odkazuje sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="230a0-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="230a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="230a0-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="230a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="230a0-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="230a0-106">[v] Cesta k sestavení k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="230a0-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="230a0-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="230a0-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="230a0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="230a0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="230a0-109">[v] Ukazatel na [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který reprezentuje sestavení, které mají být vyloučeny z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="230a0-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="230a0-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v `pwzFilePath`, s výjimkou sestavení reprezentována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="230a0-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="230a0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="230a0-111">Return Value</span></span>  
  
|<span data-ttu-id="230a0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="230a0-112">HRESULT</span></span>|<span data-ttu-id="230a0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="230a0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="230a0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="230a0-114">S_OK</span></span>|<span data-ttu-id="230a0-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="230a0-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="230a0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="230a0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="230a0-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="230a0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="230a0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="230a0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="230a0-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="230a0-119">The call timed out.</span></span>|  
|<span data-ttu-id="230a0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="230a0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="230a0-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="230a0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="230a0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="230a0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="230a0-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="230a0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="230a0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="230a0-124">E_FAIL</span></span>|<span data-ttu-id="230a0-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="230a0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="230a0-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="230a0-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="230a0-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="230a0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="230a0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="230a0-128">Remarks</span></span>  
 <span data-ttu-id="230a0-129">Volající můžete vyloučit sadu odkazy na sestavení známé z vráceném seznamu.</span><span class="sxs-lookup"><span data-stu-id="230a0-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="230a0-130">Tato sada je definována `pExcludeAssembliesList` parametr.</span><span class="sxs-lookup"><span data-stu-id="230a0-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="230a0-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="230a0-131">Requirements</span></span>  
 <span data-ttu-id="230a0-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="230a0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="230a0-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="230a0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="230a0-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="230a0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="230a0-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="230a0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230a0-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="230a0-136">See Also</span></span>  
 [<span data-ttu-id="230a0-137">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230a0-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="230a0-138">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230a0-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="230a0-139">Iclrreferenceassemblyenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="230a0-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
