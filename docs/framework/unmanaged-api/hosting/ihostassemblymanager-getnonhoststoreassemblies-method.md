---
title: "IHostAssemblyManager::GetNonHostStoreAssemblies – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager.GetNonHostStoreAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35e22e186b290cc4242275976f5109b73e2cf068
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="86e0c-102">IHostAssemblyManager::GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="86e0c-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="86e0c-103">Získá ukazatele rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , která představuje seznam sestavení, které hostitel očekává modul CLR (CLR) pro načtení.</span><span class="sxs-lookup"><span data-stu-id="86e0c-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e0c-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86e0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86e0c-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="86e0c-106">[out] Ukazatel na adresu `ICLRAssemblyReferenceList` obsahující seznam odkazů na sestavení, které hostitel očekává CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="86e0c-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86e0c-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="86e0c-107">Return Value</span></span>  
  
|<span data-ttu-id="86e0c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86e0c-108">HRESULT</span></span>|<span data-ttu-id="86e0c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="86e0c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86e0c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="86e0c-110">S_OK</span></span>|<span data-ttu-id="86e0c-111">`GetNonHostStoreAssemblies`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="86e0c-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="86e0c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86e0c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86e0c-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="86e0c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86e0c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86e0c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86e0c-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="86e0c-115">The call timed out.</span></span>|  
|<span data-ttu-id="86e0c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86e0c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86e0c-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="86e0c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86e0c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86e0c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86e0c-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="86e0c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86e0c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86e0c-120">E_FAIL</span></span>|<span data-ttu-id="86e0c-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="86e0c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86e0c-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="86e0c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86e0c-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86e0c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86e0c-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="86e0c-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="86e0c-125">Nedostatek paměti byl k dispozici pro vytvoření seznamu odkazů na požadované `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="86e0c-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e0c-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86e0c-126">Remarks</span></span>  
 <span data-ttu-id="86e0c-127">Modul CLR přeloží odkazů pomocí následující sadu pokynů:</span><span class="sxs-lookup"><span data-stu-id="86e0c-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="86e0c-128">Nejprve je zajímají seznam odkazů na sestavení vrácený `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="86e0c-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="86e0c-129">Pokud sestavení se zobrazí v seznamu, modulu CLR vytvoří vazbu k němu normálně.</span><span class="sxs-lookup"><span data-stu-id="86e0c-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="86e0c-130">Pokud v seznamu nezobrazí sestavení a hostitele poskytl implementace [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), volání CLR [ihostassemblystore::provideassembly –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) hostiteli k poskytování sestavení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="86e0c-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="86e0c-131">Modul CLR, jinak hodnota nepodaří vytvořit vazbu k sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e0c-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="86e0c-132">Pokud hostitel nastaví `ppReferenceList` na hodnotu null, první sondy CLR do globální mezipaměti sestavení, zavolá `ProvideAssembly`a pak sondy základní aplikace přeložit odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e0c-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86e0c-133">Při inicializaci modulu CLR volá `GetNonHostStoreAssemblies` pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="86e0c-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="86e0c-134">Metoda není volána znovu.</span><span class="sxs-lookup"><span data-stu-id="86e0c-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e0c-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86e0c-135">Requirements</span></span>  
 <span data-ttu-id="86e0c-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86e0c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e0c-137">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86e0c-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86e0c-138">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86e0c-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86e0c-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e0c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e0c-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="86e0c-140">See Also</span></span>  
 [<span data-ttu-id="86e0c-141">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86e0c-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="86e0c-142">Ihostassemblymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86e0c-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="86e0c-143">Ihostassemblystore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86e0c-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
