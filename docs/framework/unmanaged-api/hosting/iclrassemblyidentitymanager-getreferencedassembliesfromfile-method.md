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
ms.openlocfilehash: eac70f35e3c4c0beab0842f24702213a98fbaae3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478489"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="d0d4d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d0d4d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="d0d4d-103">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance, která obsahuje seznam sestavení odkazovaných sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0d4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d4d-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0d4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0d4d-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="d0d4d-106">[in] Cesta k sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d0d4d-107">[in] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="d0d4d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje aktuální verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d0d4d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="d0d4d-109">[in] Ukazatel [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který reprezentuje sestavení, která má být vyloučen z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="d0d4d-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identity sestavení pro sestavení odkazuje sestavení v `pwzFilePath`, s výjimkou sestavení reprezentována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0d4d-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0d4d-111">Return Value</span></span>  
  
|<span data-ttu-id="d0d4d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0d4d-112">HRESULT</span></span>|<span data-ttu-id="d0d4d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d0d4d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0d4d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0d4d-114">S_OK</span></span>|<span data-ttu-id="d0d4d-115">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="d0d4d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0d4d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0d4d-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0d4d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0d4d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0d4d-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-119">The call timed out.</span></span>|  
|<span data-ttu-id="d0d4d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0d4d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0d4d-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0d4d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0d4d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0d4d-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0d4d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0d4d-124">E_FAIL</span></span>|<span data-ttu-id="d0d4d-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0d4d-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0d4d-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0d4d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0d4d-128">Remarks</span></span>  
 <span data-ttu-id="d0d4d-129">Volající můžete zvolit ze seznamu vrácených celé sady odkazy na známé sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="d0d4d-130">Tato sada je definována `pExcludeAssembliesList` parametru.</span><span class="sxs-lookup"><span data-stu-id="d0d4d-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0d4d-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0d4d-131">Requirements</span></span>  
 <span data-ttu-id="d0d4d-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d4d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0d4d-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0d4d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0d4d-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0d4d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0d4d-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d4d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0d4d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0d4d-136">See also</span></span>
- [<span data-ttu-id="d0d4d-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d4d-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="d0d4d-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d4d-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d0d4d-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0d4d-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
