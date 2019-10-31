---
title: IHostAssemblyStore – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: d7475e2423d4dc6f57e8928514d7991169eef232
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124492"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="70922-102">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70922-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="70922-103">Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="70922-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70922-104">Metody</span><span class="sxs-lookup"><span data-stu-id="70922-104">Methods</span></span>  
  
|<span data-ttu-id="70922-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="70922-105">Method</span></span>|<span data-ttu-id="70922-106">Popis</span><span class="sxs-lookup"><span data-stu-id="70922-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70922-107">ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="70922-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="70922-108">Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , vrácený voláním metody [IHostAssemblyManager:: GetNonHostStoreAssemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="70922-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="70922-109">ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="70922-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="70922-110">Vyřeší modul v rámci sestavení nebo propojeného (nevloženého) souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="70922-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70922-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70922-111">Remarks</span></span>  
 <span data-ttu-id="70922-112">`IHostAssemblyStore` poskytuje způsob, jak může hostitel načíst sestavení efektivně na základě identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="70922-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="70922-113">Hostitel načte sestavení vrácením `IStream` instancí, které přímo odkazují na bajty.</span><span class="sxs-lookup"><span data-stu-id="70922-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="70922-114">CLR určuje, zda hostitel implementoval `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="70922-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="70922-115">To umožňuje hostiteli, například k řízení vazby na sestavení uživatelů, ale k tomu, aby se spoléhá na to, že modul runtime vytvoří vazbu na .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="70922-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70922-116">V rámci poskytování implementace `IHostAssemblyStore`hostitel Určuje svůj záměr na překlad všech sestavení, na která neodkazuje `ICLRAssemblyReferenceList` vrácených z `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="70922-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70922-117">.NET Framework verze 2,0 neposkytuje způsob, jak hostitel načíst nativní bitovou kopii sestavení, jak poskytuje nástroj [generátor nativních bitových kopií (Ngen. exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="70922-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70922-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70922-118">Requirements</span></span>  
 <span data-ttu-id="70922-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70922-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70922-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70922-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70922-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="70922-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70922-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70922-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70922-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70922-123">See also</span></span>

- [<span data-ttu-id="70922-124">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70922-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="70922-125">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70922-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="70922-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="70922-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
