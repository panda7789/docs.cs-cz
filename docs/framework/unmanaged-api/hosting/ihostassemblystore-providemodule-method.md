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
ms.openlocfilehash: 002f4177f19c2aae99e91e3fe1029b81e17481dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805003"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="7c42d-102">IHostAssemblyStore::ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="7c42d-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="7c42d-103">Vyřeší modul v rámci sestavení nebo propojeného (ale ne vloženého) souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="7c42d-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c42d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c42d-104">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c42d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c42d-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="7c42d-106">pro Ukazatel na instanci [modulebindinfo –](modulebindinfo-structure.md) , která popisuje požadovaný modul <xref:System.AppDomain> , sestavení a název modulu.</span><span class="sxs-lookup"><span data-stu-id="7c42d-106">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="7c42d-107">mimo Ukazatel na jedinečný identifikátor pro `IStream` obsahující načtený modul.</span><span class="sxs-lookup"><span data-stu-id="7c42d-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="7c42d-108">mimo Ukazatel na adresu `IStream` objektu, který obsahuje přenos přenosného spustitelného souboru (PE), který má být načten, nebo hodnotu null, pokud modul nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="7c42d-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="7c42d-109">mimo Ukazatel na adresu `IStream` objektu, který obsahuje informace o programovém ladění (PDB) pro požadovaný modul nebo hodnotu null, pokud nebyl nalezen soubor. pdb.</span><span class="sxs-lookup"><span data-stu-id="7c42d-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c42d-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7c42d-110">Return Value</span></span>  
  
|<span data-ttu-id="7c42d-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c42d-111">HRESULT</span></span>|<span data-ttu-id="7c42d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7c42d-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c42d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c42d-113">S_OK</span></span>|<span data-ttu-id="7c42d-114">`ProvideModule`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7c42d-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="7c42d-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c42d-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c42d-116">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7c42d-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c42d-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c42d-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c42d-118">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7c42d-118">The call timed out.</span></span>|  
|<span data-ttu-id="7c42d-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c42d-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c42d-120">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7c42d-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c42d-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c42d-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c42d-122">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7c42d-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c42d-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c42d-123">E_FAIL</span></span>|<span data-ttu-id="7c42d-124">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7c42d-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c42d-125">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7c42d-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c42d-126">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c42d-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7c42d-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="7c42d-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="7c42d-128">Požadované sestavení nebo propojený prostředek se nepovedlo najít.</span><span class="sxs-lookup"><span data-stu-id="7c42d-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="7c42d-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7c42d-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7c42d-130">`pdwModuleId`není dostatečně velká, aby obsahoval identifikátor, který chce hostitel vrátit.</span><span class="sxs-lookup"><span data-stu-id="7c42d-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c42d-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c42d-131">Remarks</span></span>  
 <span data-ttu-id="7c42d-132">Hodnota identity vrácená pro `pdwModuleId` je určena hostitelem.</span><span class="sxs-lookup"><span data-stu-id="7c42d-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="7c42d-133">Identifikátory musí být jedinečné v rámci životnosti procesu.</span><span class="sxs-lookup"><span data-stu-id="7c42d-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="7c42d-134">CLR používá tuto hodnotu jako jedinečný identifikátor pro přidružený datový proud.</span><span class="sxs-lookup"><span data-stu-id="7c42d-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="7c42d-135">Kontroluje každou hodnotu oproti hodnotám `pAssemblyId` vráceným voláními [ProvideAssembly –](ihostassemblystore-provideassembly-method.md) a proti hodnotám `pdwModuleId` vráceným jinými voláními `ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="7c42d-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="7c42d-136">Pokud hostitel vrátí stejnou hodnotu identifikátoru pro jiný `IStream` , CLR zkontroluje, zda obsah tohoto datového proudu již byl namapován.</span><span class="sxs-lookup"><span data-stu-id="7c42d-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="7c42d-137">Pokud ano, modul CLR načte existující kopii obrázku místo mapování nového.</span><span class="sxs-lookup"><span data-stu-id="7c42d-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="7c42d-138">Proto se identifikátor nesmí ani překrývat s identifikátory sestavení vrácenými z `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="7c42d-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c42d-139">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c42d-139">Requirements</span></span>  
 <span data-ttu-id="7c42d-140">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c42d-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c42d-141">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c42d-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c42d-142">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c42d-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c42d-143">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c42d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c42d-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c42d-144">See also</span></span>

- [<span data-ttu-id="7c42d-145">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c42d-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7c42d-146">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c42d-146">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="7c42d-147">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c42d-147">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
