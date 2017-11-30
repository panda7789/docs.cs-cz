---
title: "IHostAssemblyStore::ProvideModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6894d15221b8ace12e76b8eba4ac69503eaa792d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="fcd7b-102">IHostAssemblyStore::ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="fcd7b-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="fcd7b-103">Přeloží souboru prostředků modulu v sestavení nebo spojen (ale nikoli vložené).</span><span class="sxs-lookup"><span data-stu-id="fcd7b-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcd7b-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcd7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcd7b-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="fcd7b-106">[v] Ukazatel [modulebindinfo –](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instanci, která popisuje požadovaný modul <xref:System.AppDomain>, sestavení a název modulu.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="fcd7b-107">[out] Ukazatel na jedinečný identifikátor `IStream` obsahující načíst modul.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="fcd7b-108">[out] Ukazatel na adresu `IStream` objektu, který obsahuje bitovou kopii přenosné spustitelný soubor (PE) mají být načteny, nebo hodnota null, pokud modul nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="fcd7b-109">[out] Ukazatel na adresu `IStream` objektu, který obsahuje informace o ladění (PDB) program pro požadovaný modul, nebo hodnota null, pokud na soubor .pdb nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcd7b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fcd7b-110">Return Value</span></span>  
  
|<span data-ttu-id="fcd7b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fcd7b-111">HRESULT</span></span>|<span data-ttu-id="fcd7b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fcd7b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fcd7b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fcd7b-113">S_OK</span></span>|<span data-ttu-id="fcd7b-114">`ProvideModule`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="fcd7b-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fcd7b-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fcd7b-116">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fcd7b-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fcd7b-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fcd7b-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-118">The call timed out.</span></span>|  
|<span data-ttu-id="fcd7b-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fcd7b-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fcd7b-120">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fcd7b-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fcd7b-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fcd7b-122">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fcd7b-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fcd7b-123">E_FAIL</span></span>|<span data-ttu-id="fcd7b-124">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fcd7b-125">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fcd7b-126">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fcd7b-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="fcd7b-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="fcd7b-128">Nelze najít požadovaný sestavení nebo propojeného prostředku.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="fcd7b-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="fcd7b-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="fcd7b-130">`pdwModuleId`není dostatečně velký, aby se tak, aby obsahovala identifikátor, který chce vrátit hostitele.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcd7b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcd7b-131">Remarks</span></span>  
 <span data-ttu-id="fcd7b-132">Vrátí hodnotu identity pro `pdwModuleId` je zadán pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="fcd7b-133">Identifikátory musí být jedinečný v rámci životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="fcd7b-134">Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružené datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="fcd7b-135">Zkontroluje s hodnotami pro každou hodnotu `pAssemblyId` vrácený volání [provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) a s hodnotami pro `pdwModuleId` vrácený další volání `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="fcd7b-136">Pokud hostitel vrací stejnou hodnotu, identifikátor pro jinou `IStream`, modul CLR kontroluje, zda jste již namapována obsah tohoto datového proudu.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="fcd7b-137">Pokud ano, modulu CLR načte existující kopii místo mapování novou.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="fcd7b-138">Proto nesmí identifikátor také překrývat s identifikátory sestavení vrácená z `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="fcd7b-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcd7b-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcd7b-139">Requirements</span></span>  
 <span data-ttu-id="fcd7b-140">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcd7b-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcd7b-141">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fcd7b-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fcd7b-142">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fcd7b-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fcd7b-143">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcd7b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcd7b-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="fcd7b-144">See Also</span></span>  
 [<span data-ttu-id="fcd7b-145">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcd7b-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="fcd7b-146">Ihostassemblymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcd7b-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="fcd7b-147">Ihostassemblystore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fcd7b-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
