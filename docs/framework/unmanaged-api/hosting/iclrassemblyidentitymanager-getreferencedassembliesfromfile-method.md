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
ms.openlocfilehash: 6ba3ea7fe7b0182971899066f2cee63804fddbd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127826"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="2b4d2-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="2b4d2-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="2b4d2-103">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance, která obsahuje seznam sestavení odkazovaných sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b4d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b4d2-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b4d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b4d2-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="2b4d2-106">[in] Cesta k sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2b4d2-107">[in] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="2b4d2-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje aktuální verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="2b4d2-109">[in] Ukazatel [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který reprezentuje sestavení, která má být vyloučen z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="2b4d2-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identity sestavení pro sestavení odkazuje sestavení v `pwzFilePath`, s výjimkou sestavení reprezentována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b4d2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b4d2-111">Return Value</span></span>  
  
|<span data-ttu-id="2b4d2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b4d2-112">HRESULT</span></span>|<span data-ttu-id="2b4d2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2b4d2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b4d2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b4d2-114">S_OK</span></span>|<span data-ttu-id="2b4d2-115">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="2b4d2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b4d2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b4d2-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b4d2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b4d2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b4d2-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-119">The call timed out.</span></span>|  
|<span data-ttu-id="2b4d2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b4d2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b4d2-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b4d2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b4d2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b4d2-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b4d2-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b4d2-124">E_FAIL</span></span>|<span data-ttu-id="2b4d2-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b4d2-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b4d2-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b4d2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b4d2-128">Remarks</span></span>  
 <span data-ttu-id="2b4d2-129">Volající můžete zvolit ze seznamu vrácených celé sady odkazy na známé sestavení.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="2b4d2-130">Tato sada je definována `pExcludeAssembliesList` parametru.</span><span class="sxs-lookup"><span data-stu-id="2b4d2-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b4d2-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b4d2-131">Requirements</span></span>  
 <span data-ttu-id="2b4d2-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b4d2-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b4d2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b4d2-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b4d2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b4d2-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4d2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b4d2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b4d2-136">See also</span></span>

- [<span data-ttu-id="2b4d2-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b4d2-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2b4d2-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b4d2-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2b4d2-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b4d2-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
