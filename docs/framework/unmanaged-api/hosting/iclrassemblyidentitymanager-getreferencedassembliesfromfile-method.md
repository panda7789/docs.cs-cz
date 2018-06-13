---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 721cf93f1edecfc347c5ab6efa056aebd4dc6f9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434158"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="1e451-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="1e451-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="1e451-103">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instanci, která obsahuje seznam sestavení odkazuje sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="1e451-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e451-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e451-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e451-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e451-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="1e451-106">[v] Cesta k sestavení k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="1e451-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1e451-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="1e451-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="1e451-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1e451-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="1e451-109">[v] Ukazatel na [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který reprezentuje sestavení, které mají být vyloučeny z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="1e451-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="1e451-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v `pwzFilePath`, s výjimkou sestavení reprezentována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="1e451-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e451-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1e451-111">Return Value</span></span>  
  
|<span data-ttu-id="1e451-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e451-112">HRESULT</span></span>|<span data-ttu-id="1e451-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1e451-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e451-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e451-114">S_OK</span></span>|<span data-ttu-id="1e451-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1e451-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="1e451-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e451-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e451-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1e451-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1e451-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1e451-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1e451-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1e451-119">The call timed out.</span></span>|  
|<span data-ttu-id="1e451-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1e451-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1e451-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="1e451-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1e451-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1e451-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1e451-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="1e451-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1e451-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e451-124">E_FAIL</span></span>|<span data-ttu-id="1e451-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="1e451-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1e451-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="1e451-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1e451-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1e451-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e451-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e451-128">Remarks</span></span>  
 <span data-ttu-id="1e451-129">Volající můžete vyloučit sadu odkazy na sestavení známé z vráceném seznamu.</span><span class="sxs-lookup"><span data-stu-id="1e451-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="1e451-130">Tato sada je definována `pExcludeAssembliesList` parametr.</span><span class="sxs-lookup"><span data-stu-id="1e451-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e451-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e451-131">Requirements</span></span>  
 <span data-ttu-id="1e451-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e451-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e451-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e451-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e451-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1e451-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e451-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e451-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e451-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e451-136">See Also</span></span>  
 [<span data-ttu-id="1e451-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e451-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="1e451-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e451-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="1e451-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1e451-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
