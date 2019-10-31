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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124489"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="5b8e2-102">IHostAssemblyStore::ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="5b8e2-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="5b8e2-103">Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který se vrací z [IHostAssemblyManager:: GetNonHostStoreAssemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b8e2-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="5b8e2-104">Modul CLR (Common Language Runtime) `ProvideAssembly` volá pro každé sestavení, které se nezobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b8e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b8e2-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b8e2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b8e2-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="5b8e2-107">pro Ukazatel na instanci [assemblybindinfo –](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) , kterou hostitel používá k určení určitých vlastností vazby, včetně přítomnosti nebo nepřítomnosti jakékoli zásady správy verzí a sestavení, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="5b8e2-108">mimo Ukazatel na jedinečný identifikátor pro požadované sestavení pro tento `IStream`.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="5b8e2-109">mimo Ukazatel na data specifická pro hostitele, která se používají k určení legitimace požadovaného sestavení bez nutnosti vyvolání volání platformy.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="5b8e2-110">`pHostContext` odpovídá vlastnosti <xref:System.Reflection.Assembly.HostContext%2A> spravované třídy <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="5b8e2-111">mimo Ukazatel na adresu `IStream` obsahující přenosné spustitelné soubory (PE), které mají být načteny, nebo hodnotu null, pokud nebylo nalezeno sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="5b8e2-112">mimo Ukazatel na adresu `IStream`, který obsahuje informace o ladění programu (PDB), nebo hodnotu null, pokud se nepovedlo najít soubor. pdb.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b8e2-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5b8e2-113">Return Value</span></span>  
  
|<span data-ttu-id="5b8e2-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b8e2-114">HRESULT</span></span>|<span data-ttu-id="5b8e2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5b8e2-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b8e2-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b8e2-116">S_OK</span></span>|<span data-ttu-id="5b8e2-117">`ProvideAssembly` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="5b8e2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b8e2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b8e2-119">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b8e2-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b8e2-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b8e2-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-121">The call timed out.</span></span>|  
|<span data-ttu-id="5b8e2-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b8e2-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b8e2-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b8e2-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b8e2-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b8e2-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b8e2-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b8e2-126">E_FAIL</span></span>|<span data-ttu-id="5b8e2-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b8e2-128">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b8e2-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5b8e2-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="5b8e2-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="5b8e2-131">Požadované sestavení nebylo nalezeno.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="5b8e2-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5b8e2-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5b8e2-133">Velikost vyrovnávací paměti určená `pAssemblyId` není dostatečně velká pro uložení identifikátoru, který chce hostitel vrátit.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b8e2-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b8e2-134">Remarks</span></span>  
 <span data-ttu-id="5b8e2-135">Hodnota identity vrácená pro `pAssemblyId` je určena hostitelem.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="5b8e2-136">Identifikátory musí být jedinečné v rámci životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="5b8e2-137">CLR používá tuto hodnotu jako jedinečný identifikátor pro datový proud.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="5b8e2-138">Kontroluje každou hodnotu proti hodnotám `pAssemblyId` vrácených jinými voláními `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="5b8e2-139">Pokud hostitel vrátí stejnou `pAssemblyId` hodnotu pro jiný `IStream`, CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="5b8e2-140">Pokud ano, modul runtime načte existující kopii obrázku místo mapování nového.</span><span class="sxs-lookup"><span data-stu-id="5b8e2-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b8e2-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b8e2-141">Requirements</span></span>  
 <span data-ttu-id="5b8e2-142">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b8e2-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b8e2-143">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b8e2-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b8e2-144">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b8e2-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b8e2-145">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b8e2-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b8e2-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b8e2-146">See also</span></span>

- [<span data-ttu-id="5b8e2-147">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b8e2-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="5b8e2-148">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b8e2-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="5b8e2-149">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b8e2-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
