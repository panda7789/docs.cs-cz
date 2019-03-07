---
title: IHostAssemblyManager::GetNonHostStoreAssemblies – metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85f74eb3c6f159cf2c8c8cbd186695dc97489504
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469193"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="86742-102">IHostAssemblyManager::GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="86742-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="86742-103">Získá ukazatel rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , která představuje seznam sestavení, které hostitele očekává, že modul CLR (CLR) pro načtení.</span><span class="sxs-lookup"><span data-stu-id="86742-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86742-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86742-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86742-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86742-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="86742-106">[out] Ukazatel na adresu `ICLRAssemblyReferenceList` , který obsahuje seznam odkazů na sestavení, která očekává hostitele CLR pro načtení.</span><span class="sxs-lookup"><span data-stu-id="86742-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86742-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="86742-107">Return Value</span></span>  
  
|<span data-ttu-id="86742-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86742-108">HRESULT</span></span>|<span data-ttu-id="86742-109">Popis</span><span class="sxs-lookup"><span data-stu-id="86742-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86742-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86742-110">S_OK</span></span>|<span data-ttu-id="86742-111">`GetNonHostStoreAssemblies` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="86742-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="86742-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86742-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86742-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="86742-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86742-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86742-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86742-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="86742-115">The call timed out.</span></span>|  
|<span data-ttu-id="86742-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86742-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86742-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="86742-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86742-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86742-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86742-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="86742-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86742-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86742-120">E_FAIL</span></span>|<span data-ttu-id="86742-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="86742-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86742-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="86742-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86742-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86742-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86742-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="86742-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="86742-125">Nedostatek paměti nebyl k dispozici k vytvoření seznamu odkazů pro požadovanou `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="86742-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86742-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86742-126">Remarks</span></span>  
 <span data-ttu-id="86742-127">Odkazy pomocí následující sadu pokynů, které překládá CLR:</span><span class="sxs-lookup"><span data-stu-id="86742-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="86742-128">Nejprve consults seznam odkazů na sestavení vrácené `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="86742-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="86742-129">Pokud sestavení se zobrazí v seznamu, CLR vytvoří vazbu k němu normálně.</span><span class="sxs-lookup"><span data-stu-id="86742-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="86742-130">Pokud sestavení se nezobrazují v seznamu a hostitel poskytuje implementaci [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), volání CLR [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) umožňující hostitele slouží k poskytování sestavení k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="86742-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="86742-131">V opačném případě CLR nezdaří k vytvoření vazby na sestavení.</span><span class="sxs-lookup"><span data-stu-id="86742-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="86742-132">Pokud hostitel nastaví `ppReferenceList` na hodnotu null, první sond CLR volá do globální mezipaměti sestavení, `ProvideAssembly`a potom sondy základ cesty aplikace přeložit odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="86742-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86742-133">Při inicializaci, kterou volá CLR `GetNonHostStoreAssemblies` pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="86742-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="86742-134">Metoda není volána znovu.</span><span class="sxs-lookup"><span data-stu-id="86742-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86742-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86742-135">Requirements</span></span>  
 <span data-ttu-id="86742-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86742-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86742-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86742-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86742-138">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86742-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86742-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86742-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86742-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86742-140">See also</span></span>
- [<span data-ttu-id="86742-141">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86742-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="86742-142">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86742-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="86742-143">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86742-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
