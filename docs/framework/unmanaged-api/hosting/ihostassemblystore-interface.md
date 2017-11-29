---
title: "IHostAssemblyStore – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="23b55-102">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23b55-102">IHostAssemblyStore Interface</span></span>
<span data-ttu-id="23b55-103">Poskytuje metody, které umožňují hostitele k načtení sestavení a moduly nezávisle na modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="23b55-103">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23b55-104">Metody</span><span class="sxs-lookup"><span data-stu-id="23b55-104">Methods</span></span>  
  
|<span data-ttu-id="23b55-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="23b55-105">Method</span></span>|<span data-ttu-id="23b55-106">Popis</span><span class="sxs-lookup"><span data-stu-id="23b55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23b55-107">Provideassembly – metoda</span><span class="sxs-lookup"><span data-stu-id="23b55-107">ProvideAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="23b55-108">Získá odkaz na sestavení, které se odkazuje [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) vrácená z volání [ihostassemblymanager::getnonhoststoreassemblies –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="23b55-108">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="23b55-109">Providemodule – metoda</span><span class="sxs-lookup"><span data-stu-id="23b55-109">ProvideModule Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|<span data-ttu-id="23b55-110">Přeloží modulu v sestavení nebo propojené souboru prostředků (nikoli vložené).</span><span class="sxs-lookup"><span data-stu-id="23b55-110">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b55-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23b55-111">Remarks</span></span>  
 <span data-ttu-id="23b55-112">`IHostAssemblyStore`poskytuje způsob pro hostitele k načtení sestavení efektivně podle identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="23b55-112">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="23b55-113">Hostitel načte sestavení vrácením `IStream` instancí, které bod přímo na bajty.</span><span class="sxs-lookup"><span data-stu-id="23b55-113">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="23b55-114">Modul CLR Určuje, zda hostitel implementovala `IHostAssemblyStore` voláním `IHostAssemblyManager::GetNonHostAssemblyStores` při inicializaci.</span><span class="sxs-lookup"><span data-stu-id="23b55-114">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="23b55-115">To umožňuje hostiteli, například k řízení vazba k sestavení uživatele, ale závisí na modulu runtime pro vazbu na sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23b55-115">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23b55-116">Při poskytování implementace `IHostAssemblyStore`, hostitele určuje jeho záměr vyřešit všechny sestavení, které nejsou odkazuje `ICLRAssemblyReferenceList` vrácená z `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="23b55-116">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23b55-117">Rozhraní .NET Framework verze 2.0 neposkytuje způsob, jak na hostiteli a načíst nativní bitové kopie sestavení, protože poskytované [generátor (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="23b55-117">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b55-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23b55-118">Requirements</span></span>  
 <span data-ttu-id="23b55-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b55-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b55-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23b55-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23b55-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23b55-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23b55-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b55-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b55-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="23b55-123">See Also</span></span>  
 [<span data-ttu-id="23b55-124">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23b55-124">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="23b55-125">Ihostassemblymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23b55-125">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="23b55-126">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="23b55-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
