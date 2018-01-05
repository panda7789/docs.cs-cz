---
title: "ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aae8c16430f8139601a5faa2bad42e285bceb84b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="727f9-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="727f9-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="727f9-103">Získá odkazy [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="727f9-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="727f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="727f9-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="727f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="727f9-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="727f9-106">[v] Ukazatele rozhraní k `IStream` obsahující sestavení k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="727f9-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="727f9-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="727f9-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="727f9-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="727f9-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="727f9-109">[v] Ukazatel na [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který obsahuje data identit sestavení pro sestavení, které chcete vyloučit z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="727f9-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="727f9-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v `pStream`, s výjimkou sestavení v `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="727f9-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="727f9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="727f9-111">Return Value</span></span>  
  
|<span data-ttu-id="727f9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="727f9-112">HRESULT</span></span>|<span data-ttu-id="727f9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="727f9-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="727f9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="727f9-114">S_OK</span></span>|<span data-ttu-id="727f9-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="727f9-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="727f9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="727f9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="727f9-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="727f9-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="727f9-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="727f9-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="727f9-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="727f9-119">The call timed out.</span></span>|  
|<span data-ttu-id="727f9-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="727f9-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="727f9-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="727f9-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="727f9-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="727f9-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="727f9-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="727f9-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="727f9-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="727f9-124">E_FAIL</span></span>|<span data-ttu-id="727f9-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="727f9-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="727f9-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="727f9-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="727f9-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="727f9-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="727f9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="727f9-128">Remarks</span></span>  
 <span data-ttu-id="727f9-129">Volající můžete vyloučit sadu odkazy na sestavení známé z vráceném seznamu.</span><span class="sxs-lookup"><span data-stu-id="727f9-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="727f9-130">Tato sada je definována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="727f9-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="727f9-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="727f9-131">Requirements</span></span>  
 <span data-ttu-id="727f9-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="727f9-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="727f9-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="727f9-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="727f9-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="727f9-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="727f9-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="727f9-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="727f9-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="727f9-136">See Also</span></span>  
 [<span data-ttu-id="727f9-137">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="727f9-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="727f9-138">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="727f9-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="727f9-139">ICLRReferenceAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="727f9-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
