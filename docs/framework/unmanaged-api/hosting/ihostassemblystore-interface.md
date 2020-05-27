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
ms.openlocfilehash: 87fe0b10f0a1eefa8154c40d39b54285990c410c
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805034"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="c8a7d-102">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8a7d-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="c8a7d-103">Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c8a7d-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8a7d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c8a7d-104">Methods</span></span>  
  
|<span data-ttu-id="c8a7d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c8a7d-105">Method</span></span>|<span data-ttu-id="c8a7d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c8a7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8a7d-107">ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="c8a7d-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="c8a7d-108">Získá odkaz na sestavení, na které se neodkazuje [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , vrácený voláním metody [IHostAssemblyManager:: GetNonHostStoreAssemblies –](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="c8a7d-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="c8a7d-109">ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="c8a7d-109">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="c8a7d-110">Vyřeší modul v rámci sestavení nebo propojeného (nevloženého) souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="c8a7d-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8a7d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8a7d-111">Remarks</span></span>  
 <span data-ttu-id="c8a7d-112">`IHostAssemblyStore`poskytuje způsob, jak může hostitel načíst sestavení efektivně na základě identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8a7d-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="c8a7d-113">Hostitel načte sestavení vrácením `IStream` instancí, které odkazují přímo na bajty.</span><span class="sxs-lookup"><span data-stu-id="c8a7d-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="c8a7d-114">CLR určuje, zda je hostitel implementovaný `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="c8a7d-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="c8a7d-115">To umožňuje hostiteli, například k řízení vazby na sestavení uživatelů, ale k tomu, aby se spoléhá na to, že modul runtime vytvoří vazbu na .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="c8a7d-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8a7d-116">V rámci poskytování implementace `IHostAssemblyStore` , hostitel Určuje svůj záměr na překlad všech sestavení, na která neodkazuje `ICLRAssemblyReferenceList` vrácená z `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="c8a7d-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8a7d-117">.NET Framework verze 2,0 neposkytuje způsob, jak hostitel načíst nativní bitovou kopii sestavení, jak poskytuje nástroj [generátor nativních bitových kopií (Ngen. exe)](../../tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="c8a7d-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a7d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8a7d-118">Requirements</span></span>  
 <span data-ttu-id="c8a7d-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a7d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a7d-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8a7d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8a7d-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c8a7d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8a7d-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8a7d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a7d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8a7d-123">See also</span></span>

- [<span data-ttu-id="c8a7d-124">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8a7d-124">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c8a7d-125">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8a7d-125">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="c8a7d-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c8a7d-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
