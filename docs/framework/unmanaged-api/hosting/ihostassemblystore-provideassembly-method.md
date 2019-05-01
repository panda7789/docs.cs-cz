---
title: IHostAssemblyStore::ProvideAssembly – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951759"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="f97b3-102">IHostAssemblyStore::ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="f97b3-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="f97b3-103">Získá odkaz na sestavení, které neodkazují [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který je vrácen z [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="f97b3-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="f97b3-104">Common language runtime (CLR) zavolá `ProvideAssembly` pro každé sestavení, které nejsou uvedené v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f97b3-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f97b3-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f97b3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f97b3-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="f97b3-107">[in] Ukazatel na [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instanci, kterou hostitel používá k určení určité charakteristické vlastnosti vazby, včetně přítomnosti nebo nepřítomnosti všechny zásady správy verzí a sestavení, které svázat.</span><span class="sxs-lookup"><span data-stu-id="f97b3-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="f97b3-108">[out] Ukazatel na jedinečný identifikátor pro požadované sestavení pro tento `IStream`.</span><span class="sxs-lookup"><span data-stu-id="f97b3-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="f97b3-109">[out] Ukazatel na konkrétního hostitele data, která se používá k určení důkazy požadovaná sestavení bez nutnosti platformu vyvolání volání.</span><span class="sxs-lookup"><span data-stu-id="f97b3-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="f97b3-110">`pHostContext` odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnost spravovaného <xref:System.Reflection.Assembly> třídy.</span><span class="sxs-lookup"><span data-stu-id="f97b3-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="f97b3-111">[out] Ukazatel na adresu `IStream` , který obsahuje image (PE portable executable) načíst, nebo hodnota null, pokud sestavení nebylo nalezeno.</span><span class="sxs-lookup"><span data-stu-id="f97b3-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="f97b3-112">[out] Ukazatel na adresu `IStream` , který obsahuje informace o ladění (PDB) programu, nebo hodnota null, pokud soubor PDB nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="f97b3-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f97b3-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f97b3-113">Return Value</span></span>  
  
|<span data-ttu-id="f97b3-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f97b3-114">HRESULT</span></span>|<span data-ttu-id="f97b3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f97b3-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f97b3-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f97b3-116">S_OK</span></span>|<span data-ttu-id="f97b3-117">`ProvideAssembly` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f97b3-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="f97b3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f97b3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f97b3-119">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f97b3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f97b3-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f97b3-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f97b3-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f97b3-121">The call timed out.</span></span>|  
|<span data-ttu-id="f97b3-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f97b3-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f97b3-123">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f97b3-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f97b3-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f97b3-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f97b3-125">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f97b3-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f97b3-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f97b3-126">E_FAIL</span></span>|<span data-ttu-id="f97b3-127">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f97b3-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f97b3-128">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f97b3-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f97b3-129">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f97b3-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f97b3-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="f97b3-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="f97b3-131">Požadované sestavení nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="f97b3-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="f97b3-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f97b3-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f97b3-133">Velikost vyrovnávací paměti určené `pAssemblyId` není dostatečně velký pro identifikátor, který chce vrátit hostitele.</span><span class="sxs-lookup"><span data-stu-id="f97b3-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f97b3-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f97b3-134">Remarks</span></span>  
 <span data-ttu-id="f97b3-135">Vrátí hodnotu identity pro `pAssemblyId` zadaná hostitelem.</span><span class="sxs-lookup"><span data-stu-id="f97b3-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="f97b3-136">Identifikátory musí být jedinečné v rámci životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="f97b3-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="f97b3-137">Modul CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="f97b3-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="f97b3-138">Zkontroluje každou hodnotu s hodnotami pro `pAssemblyId` vrácený další volání `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="f97b3-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="f97b3-139">Pokud hostitel vrátí stejné `pAssemblyId` hodnota dalších `IStream`, CLR kontroluje, zda již byly namapovány obsah tohoto datového proudu.</span><span class="sxs-lookup"><span data-stu-id="f97b3-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="f97b3-140">Pokud ano, načte modul runtime stávající bitovou místo mapování novou kopii.</span><span class="sxs-lookup"><span data-stu-id="f97b3-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f97b3-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f97b3-141">Requirements</span></span>  
 <span data-ttu-id="f97b3-142">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f97b3-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f97b3-143">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f97b3-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f97b3-144">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f97b3-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f97b3-145">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f97b3-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f97b3-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f97b3-146">See also</span></span>

- [<span data-ttu-id="f97b3-147">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f97b3-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f97b3-148">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f97b3-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="f97b3-149">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f97b3-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
