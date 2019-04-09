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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173417"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="b129d-102">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b129d-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="b129d-103">Poskytuje metody, které umožňují hostitele k načtení sestavení a moduly bez ohledu na jejich common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b129d-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b129d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b129d-104">Methods</span></span>  
  
|<span data-ttu-id="b129d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b129d-105">Method</span></span>|<span data-ttu-id="b129d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b129d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b129d-107">ProvideAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="b129d-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="b129d-108">Získá odkaz na sestavení, které neodkazují [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) vrácená z volání [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="b129d-109">ProvideModule – metoda</span><span class="sxs-lookup"><span data-stu-id="b129d-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="b129d-110">Odstraňuje se modul v rámci sestavení nebo propojený soubor prostředků (nikoli vložené).</span><span class="sxs-lookup"><span data-stu-id="b129d-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b129d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b129d-111">Remarks</span></span>  
 `IHostAssemblyStore` <span data-ttu-id="b129d-112">poskytuje způsob pro hostitele k načtení sestavení efektivně podle identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="b129d-112">provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="b129d-113">Hostitel načte sestavení tak, že vrací `IStream` instancí, které přejděte přímo na bajty.</span><span class="sxs-lookup"><span data-stu-id="b129d-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="b129d-114">Modul CLR Určuje, zda má hostitel implementovány `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="b129d-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="b129d-115">To umožňuje hostiteli, například ovládací prvek vazby na sestavení uživatele, ale závisí na modul runtime k vytvoření vazby na sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b129d-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b129d-116">Při poskytování implementace `IHostAssemblyStore`, hostitele určuje jeho cílem je vyřešit všechna sestavení, které neodkazují `ICLRAssemblyReferenceList` vrácená `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="b129d-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b129d-117">Rozhraní .NET Framework verze 2.0 podle neposkytuje způsob, jakým hostitele k načtení nativních bitových kopií sestavení, [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="b129d-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b129d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b129d-118">Requirements</span></span>  
 <span data-ttu-id="b129d-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b129d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b129d-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b129d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b129d-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b129d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b129d-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b129d-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b129d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b129d-123">See also</span></span>

- [<span data-ttu-id="b129d-124">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b129d-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b129d-125">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b129d-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="b129d-126">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="b129d-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
