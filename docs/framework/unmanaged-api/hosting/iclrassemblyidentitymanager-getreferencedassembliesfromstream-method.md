---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream – metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d6f93ee7870c9d81394ee55c5574c52c2aea50a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969972"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="af27c-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="af27c-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="af27c-103">Získá ukazatel [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objekt, který obsahuje data identity sestavení pro sestavení odkazuje na sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="af27c-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af27c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af27c-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af27c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af27c-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="af27c-106">[in] Ukazatel rozhraní k `IStream` obsahujícího sestavení, který se má vyhodnotit.</span><span class="sxs-lookup"><span data-stu-id="af27c-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="af27c-107">[in] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="af27c-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="af27c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je hodnota, která podporuje aktuální verzi modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="af27c-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="af27c-109">[in] Ukazatel [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který obsahuje data identity sestavení pro sestavení, které se mají vyloučit z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="af27c-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="af27c-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identity sestavení pro sestavení odkazuje na sestavení v `pStream`, s výjimkou sestavení v `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="af27c-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af27c-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="af27c-111">Return Value</span></span>  
  
|<span data-ttu-id="af27c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af27c-112">HRESULT</span></span>|<span data-ttu-id="af27c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="af27c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af27c-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="af27c-114">S_OK</span></span>|<span data-ttu-id="af27c-115">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="af27c-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="af27c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af27c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af27c-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="af27c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af27c-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af27c-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af27c-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="af27c-119">The call timed out.</span></span>|  
|<span data-ttu-id="af27c-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af27c-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af27c-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="af27c-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af27c-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af27c-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af27c-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="af27c-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af27c-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af27c-124">E_FAIL</span></span>|<span data-ttu-id="af27c-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="af27c-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af27c-126">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="af27c-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af27c-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="af27c-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af27c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af27c-128">Remarks</span></span>  
 <span data-ttu-id="af27c-129">Volající můžete zvolit ze seznamu vrácených celé sady odkazy na známé sestavení.</span><span class="sxs-lookup"><span data-stu-id="af27c-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="af27c-130">Tato sada je definována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="af27c-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af27c-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af27c-131">Requirements</span></span>  
 <span data-ttu-id="af27c-132">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af27c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af27c-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af27c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af27c-134">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af27c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af27c-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af27c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af27c-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af27c-136">See also</span></span>

- [<span data-ttu-id="af27c-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af27c-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="af27c-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af27c-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="af27c-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af27c-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
