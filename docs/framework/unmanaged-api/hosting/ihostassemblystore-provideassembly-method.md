---
title: "IHostAssemblyStore::ProvideAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="4b9b3-102">IHostAssemblyStore::ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="4b9b3-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="4b9b3-103">Získá odkaz na sestavení, které se odkazuje [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , je vrácena z [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="4b9b3-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="4b9b3-104">Modul CLR (CLR) volá `ProvideAssembly` pro každé sestavení, který se nenachází v seznamu.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b9b3-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b9b3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b9b3-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="4b9b3-107">[v] Ukazatel na [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance, který hostitel používá k určení určité charakteristické vlastnosti vazby, včetně existenci nebo neexistenci těchto všechny zásady správy verzí a které sestavení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="4b9b3-108">[out] Ukazatel na jedinečný identifikátor pro požadovaný sestavení pro tento `IStream`.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="4b9b3-109">[out] Ukazatel na konkrétním hostiteli data, která se používá k určení důkaz požadovaný sestavení bez nutnosti platformy vyvolat volání.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="4b9b3-110">`pHostContext`odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnost spravovaný <xref:System.Reflection.Assembly> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="4b9b3-111">[out] Ukazatel na adresu `IStream` obsahující přenosné spustitelný soubor (PE) obrázek, který má být načten nebo hodnota null, pokud je sestavení nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="4b9b3-112">[out] Ukazatel na adresu `IStream` obsahující informace o ladění (PDB) programu, nebo hodnota null, pokud na soubor .pdb nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b9b3-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4b9b3-113">Return Value</span></span>  
  
|<span data-ttu-id="4b9b3-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b9b3-114">HRESULT</span></span>|<span data-ttu-id="4b9b3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4b9b3-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b9b3-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b9b3-116">S_OK</span></span>|<span data-ttu-id="4b9b3-117">`ProvideAssembly`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="4b9b3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b9b3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b9b3-119">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b9b3-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b9b3-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b9b3-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-121">The call timed out.</span></span>|  
|<span data-ttu-id="4b9b3-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b9b3-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b9b3-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b9b3-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b9b3-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b9b3-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b9b3-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b9b3-126">E_FAIL</span></span>|<span data-ttu-id="4b9b3-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b9b3-128">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b9b3-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4b9b3-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="4b9b3-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="4b9b3-131">Požadovaný sestavení nelze najít.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="4b9b3-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4b9b3-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4b9b3-133">Zadaná velikost vyrovnávací paměti podle `pAssemblyId` není dostatečně velký pro uložení identifikátor, který chce vrátit hostitele.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b9b3-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b9b3-134">Remarks</span></span>  
 <span data-ttu-id="4b9b3-135">Vrátí hodnotu identity pro `pAssemblyId` je zadán pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="4b9b3-136">Identifikátory musí být jedinečný v rámci životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="4b9b3-137">Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="4b9b3-138">Zkontroluje s hodnotami pro každou hodnotu `pAssemblyId` vrácený další volání `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="4b9b3-139">Pokud hostitel vrátí stejné `pAssemblyId` hodnotu pro jinou `IStream`, modul CLR kontroluje, zda jste již namapována obsah tohoto datového proudu.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="4b9b3-140">Pokud ano, načte modul runtime existující kopii místo mapování novou.</span><span class="sxs-lookup"><span data-stu-id="4b9b3-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b9b3-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b9b3-141">Requirements</span></span>  
 <span data-ttu-id="4b9b3-142">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b9b3-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b9b3-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4b9b3-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b9b3-144">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b9b3-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b9b3-145">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b9b3-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9b3-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b9b3-146">See Also</span></span>  
 [<span data-ttu-id="4b9b3-147">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b9b3-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4b9b3-148">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b9b3-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="4b9b3-149">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b9b3-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
