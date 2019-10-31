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
ms.openlocfilehash: eb715e1a4f9a210a1440874a9a8cea2d85345d33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124580"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="4f3e9-102">IHostAssemblyManager::GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="4f3e9-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="4f3e9-103">Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="4f3e9-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f3e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f3e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f3e9-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="4f3e9-106">mimo Ukazatel na adresu `ICLRAssemblyReferenceList`, která obsahuje seznam odkazů na sestavení, která hostitel očekává načtení CLR.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f3e9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4f3e9-107">Return Value</span></span>  
  
|<span data-ttu-id="4f3e9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f3e9-108">HRESULT</span></span>|<span data-ttu-id="4f3e9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4f3e9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f3e9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f3e9-110">S_OK</span></span>|<span data-ttu-id="4f3e9-111">`GetNonHostStoreAssemblies` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="4f3e9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f3e9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f3e9-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f3e9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f3e9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f3e9-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-115">The call timed out.</span></span>|  
|<span data-ttu-id="4f3e9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f3e9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f3e9-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f3e9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f3e9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f3e9-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f3e9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f3e9-120">E_FAIL</span></span>|<span data-ttu-id="4f3e9-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f3e9-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f3e9-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4f3e9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4f3e9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4f3e9-125">Není k dispozici dostatek paměti pro vytvoření seznamu odkazů pro požadovaný `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f3e9-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f3e9-126">Remarks</span></span>  
 <span data-ttu-id="4f3e9-127">CLR vyřeší odkazy pomocí následující sady pokynů:</span><span class="sxs-lookup"><span data-stu-id="4f3e9-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="4f3e9-128">Nejprve se poraďte se seznamem odkazů na sestavení vrácených `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="4f3e9-129">Pokud se v seznamu objeví sestavení, CLR se k němu váže normálně.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="4f3e9-130">Pokud se sestavení v seznamu nezobrazí a hostitel zavedl implementaci [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR volá [IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , aby hostitel mohl poskytnout sestavení pro svázání.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="4f3e9-131">V opačném případě se modul CLR nemůže připojit k sestavení.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="4f3e9-132">Pokud se `ppReferenceList` hostitelů nastaví na hodnotu null, modul CLR nejprve testuje globální mezipaměť sestavení (GAC), zavolá `ProvideAssembly`a pak vyhledá základ aplikace, aby vyřešil odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f3e9-133">Po inicializaci CLR volá `GetNonHostStoreAssemblies` pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="4f3e9-134">Metoda není volána znovu.</span><span class="sxs-lookup"><span data-stu-id="4f3e9-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f3e9-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f3e9-135">Requirements</span></span>  
 <span data-ttu-id="4f3e9-136">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f3e9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f3e9-137">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4f3e9-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f3e9-138">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f3e9-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f3e9-139">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f3e9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3e9-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f3e9-140">See also</span></span>

- [<span data-ttu-id="4f3e9-141">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f3e9-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4f3e9-142">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f3e9-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="4f3e9-143">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f3e9-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
