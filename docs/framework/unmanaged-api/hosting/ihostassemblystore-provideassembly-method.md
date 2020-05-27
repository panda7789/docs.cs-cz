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
ms.openlocfilehash: f97490e89e835716911072dbad5f70d8e55e76e6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805020"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="cbeca-102">IHostAssemblyStore::ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="cbeca-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="cbeca-103">Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který se vrací z [IHostAssemblyManager:: GetNonHostStoreAssemblies –](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="cbeca-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="cbeca-104">Modul CLR (Common Language Runtime) volá `ProvideAssembly` pro každé sestavení, které se v seznamu nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="cbeca-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbeca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbeca-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbeca-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cbeca-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="cbeca-107">pro Ukazatel na instanci [assemblybindinfo –](assemblybindinfo-structure.md) , kterou hostitel používá k určení určitých vlastností vazby, včetně přítomnosti nebo nepřítomnosti jakékoli zásady správy verzí a sestavení, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="cbeca-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="cbeca-108">mimo Ukazatel na jedinečný identifikátor pro požadované sestavení `IStream` .</span><span class="sxs-lookup"><span data-stu-id="cbeca-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="cbeca-109">mimo Ukazatel na data specifická pro hostitele, která se používají k určení legitimace požadovaného sestavení bez nutnosti vyvolání volání platformy.</span><span class="sxs-lookup"><span data-stu-id="cbeca-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="cbeca-110">`pHostContext`odpovídá <xref:System.Reflection.Assembly.HostContext%2A> vlastnosti spravované <xref:System.Reflection.Assembly> třídy.</span><span class="sxs-lookup"><span data-stu-id="cbeca-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="cbeca-111">mimo Ukazatel na adresu obsahující `IStream` přenos přenosného spustitelného souboru (PE), který má být načten, nebo hodnotu null, pokud nebylo nalezeno sestavení.</span><span class="sxs-lookup"><span data-stu-id="cbeca-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="cbeca-112">mimo Ukazatel na adresu obsahující `IStream` informace o programovém ladění (PDB) nebo hodnotu null, pokud soubor. pdb nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="cbeca-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbeca-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cbeca-113">Return Value</span></span>  
  
|<span data-ttu-id="cbeca-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbeca-114">HRESULT</span></span>|<span data-ttu-id="cbeca-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cbeca-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbeca-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbeca-116">S_OK</span></span>|<span data-ttu-id="cbeca-117">`ProvideAssembly`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="cbeca-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="cbeca-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbeca-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbeca-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="cbeca-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbeca-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbeca-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbeca-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="cbeca-121">The call timed out.</span></span>|  
|<span data-ttu-id="cbeca-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbeca-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbeca-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="cbeca-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbeca-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbeca-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbeca-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="cbeca-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbeca-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbeca-126">E_FAIL</span></span>|<span data-ttu-id="cbeca-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="cbeca-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cbeca-128">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="cbeca-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbeca-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cbeca-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cbeca-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="cbeca-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="cbeca-131">Požadované sestavení nebylo nalezeno.</span><span class="sxs-lookup"><span data-stu-id="cbeca-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="cbeca-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="cbeca-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="cbeca-133">Velikost vyrovnávací paměti určená parametrem není `pAssemblyId` dostatečně velká pro uložení identifikátoru, který chce hostitel vrátit.</span><span class="sxs-lookup"><span data-stu-id="cbeca-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbeca-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbeca-134">Remarks</span></span>  
 <span data-ttu-id="cbeca-135">Hodnota identity vrácená pro `pAssemblyId` je určena hostitelem.</span><span class="sxs-lookup"><span data-stu-id="cbeca-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="cbeca-136">Identifikátory musí být jedinečné v rámci životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="cbeca-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="cbeca-137">CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="cbeca-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="cbeca-138">Kontroluje každou hodnotu oproti hodnotám `pAssemblyId` vráceným jinými voláními `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="cbeca-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="cbeca-139">Pokud hostitel vrátí stejnou `pAssemblyId` hodnotu pro jiný `IStream` , CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován.</span><span class="sxs-lookup"><span data-stu-id="cbeca-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="cbeca-140">Pokud ano, modul runtime načte existující kopii obrázku místo mapování nového.</span><span class="sxs-lookup"><span data-stu-id="cbeca-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbeca-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbeca-141">Requirements</span></span>  
 <span data-ttu-id="cbeca-142">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbeca-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbeca-143">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbeca-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbeca-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbeca-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbeca-145">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbeca-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbeca-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbeca-146">See also</span></span>

- [<span data-ttu-id="cbeca-147">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbeca-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="cbeca-148">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbeca-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="cbeca-149">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbeca-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
