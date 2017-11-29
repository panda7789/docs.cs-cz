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
ms.openlocfilehash: 64a43640d08acbab0bcf505cc8a5850784ff18ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="d4315-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d4315-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="d4315-103">Získá odkazy [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d4315-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4315-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4315-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4315-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4315-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="d4315-106">[v] Ukazatele rozhraní k `IStream` obsahující sestavení k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="d4315-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d4315-107">[v] K dispozici pro budoucí rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d4315-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="d4315-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT je jediná hodnota, která podporuje verzí common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d4315-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="d4315-109">[v] Ukazatel na [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) objekt, který obsahuje data identit sestavení pro sestavení, které chcete vyloučit z `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="d4315-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="d4315-110">[out] Ukazatel na adresu `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v `pStream`, s výjimkou sestavení v `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="d4315-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4315-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4315-111">Return Value</span></span>  
  
|<span data-ttu-id="d4315-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4315-112">HRESULT</span></span>|<span data-ttu-id="d4315-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d4315-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4315-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4315-114">S_OK</span></span>|<span data-ttu-id="d4315-115">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d4315-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="d4315-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4315-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4315-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d4315-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4315-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4315-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4315-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d4315-119">The call timed out.</span></span>|  
|<span data-ttu-id="d4315-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4315-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4315-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="d4315-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4315-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4315-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4315-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="d4315-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4315-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4315-124">E_FAIL</span></span>|<span data-ttu-id="d4315-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="d4315-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4315-126">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d4315-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4315-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d4315-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4315-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4315-128">Remarks</span></span>  
 <span data-ttu-id="d4315-129">Volající můžete vyloučit sadu odkazy na sestavení známé z vráceném seznamu.</span><span class="sxs-lookup"><span data-stu-id="d4315-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="d4315-130">Tato sada je definována `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="d4315-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4315-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4315-131">Requirements</span></span>  
 <span data-ttu-id="d4315-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4315-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4315-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4315-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4315-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4315-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4315-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4315-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4315-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4315-136">See Also</span></span>  
 [<span data-ttu-id="d4315-137">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4315-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="d4315-138">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4315-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d4315-139">Iclrreferenceassemblyenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4315-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
