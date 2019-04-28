---
title: IHostAssemblyStore::ProvideModule – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599339"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="d778d-102">IHostAssemblyStore::ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="d778d-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="d778d-103">Přeloží do souboru prostředků modulu v sestavení nebo propojená (ale nikoli vložené).</span><span class="sxs-lookup"><span data-stu-id="d778d-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d778d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d778d-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d778d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d778d-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="d778d-106">[in] Ukazatel [modulebindinfo –](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instanci, která popisuje požadovaný modul <xref:System.AppDomain>, sestavení a název modulu.</span><span class="sxs-lookup"><span data-stu-id="d778d-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="d778d-107">[out] Ukazatel na jedinečný identifikátor `IStream` obsahující načteného modulu.</span><span class="sxs-lookup"><span data-stu-id="d778d-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="d778d-108">[out] Ukazatel na adresu `IStream` objekt, který obsahuje image (PE portable executable) mají být načteny, nebo hodnota null, pokud modul nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="d778d-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="d778d-109">[out] Ukazatel na adresu `IStream` objekt, který obsahuje informace o ladění (PDB) programu požadované pro modul, nebo hodnota null, pokud soubor PDB nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="d778d-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d778d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d778d-110">Return Value</span></span>  
  
|<span data-ttu-id="d778d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d778d-111">HRESULT</span></span>|<span data-ttu-id="d778d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d778d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d778d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d778d-113">S_OK</span></span>|<span data-ttu-id="d778d-114">`ProvideModule` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d778d-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="d778d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d778d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d778d-116">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d778d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d778d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d778d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d778d-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d778d-118">The call timed out.</span></span>|  
|<span data-ttu-id="d778d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d778d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d778d-120">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d778d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d778d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d778d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d778d-122">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d778d-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d778d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d778d-123">E_FAIL</span></span>|<span data-ttu-id="d778d-124">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d778d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d778d-125">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d778d-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d778d-126">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d778d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d778d-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="d778d-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="d778d-128">Požadované sestavení nebo propojeného prostředku nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="d778d-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="d778d-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d778d-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d778d-130">`pdwModuleId` není dostatečně velký, aby obsahovat identifikátor, který chce vrátit hostitele.</span><span class="sxs-lookup"><span data-stu-id="d778d-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d778d-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d778d-131">Remarks</span></span>  
 <span data-ttu-id="d778d-132">Vrátí hodnotu identity pro `pdwModuleId` zadaná hostitelem.</span><span class="sxs-lookup"><span data-stu-id="d778d-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="d778d-133">Identifikátory musí být jedinečné v rámci životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="d778d-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="d778d-134">Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružené datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d778d-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="d778d-135">Zkontroluje každou hodnotu s hodnotami pro `pAssemblyId` vrácený volání [provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) a s hodnotami pro `pdwModuleId` vrácený další volání `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="d778d-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="d778d-136">Pokud hostitel vrátí stejnou hodnotu identifikátoru dalších `IStream`, CLR kontroluje, zda již byly namapovány obsah tohoto datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d778d-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="d778d-137">Pokud ano, načte modul CLR stávající bitovou místo mapování novou kopii.</span><span class="sxs-lookup"><span data-stu-id="d778d-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="d778d-138">Proto nesmí identifikátor také překrývat s identifikátory sestavení vrácená `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="d778d-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d778d-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d778d-139">Requirements</span></span>  
 <span data-ttu-id="d778d-140">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d778d-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d778d-141">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d778d-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d778d-142">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d778d-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d778d-143">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d778d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d778d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d778d-144">See also</span></span>

- [<span data-ttu-id="d778d-145">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d778d-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d778d-146">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d778d-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="d778d-147">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d778d-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
