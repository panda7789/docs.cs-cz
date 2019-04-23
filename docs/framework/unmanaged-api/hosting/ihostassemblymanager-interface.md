---
title: IHostAssemblyManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118947"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="65855-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65855-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="65855-103">Poskytuje metody, které povolí hostitelské zadat sadu sestavení, které se mají načíst modulem common language runtime (CLR) nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="65855-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65855-104">Metody</span><span class="sxs-lookup"><span data-stu-id="65855-104">Methods</span></span>  
  
|<span data-ttu-id="65855-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="65855-105">Method</span></span>|<span data-ttu-id="65855-106">Popis</span><span class="sxs-lookup"><span data-stu-id="65855-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65855-107">GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="65855-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="65855-108">Získá ukazatel rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení zavedených od hostitele.</span><span class="sxs-lookup"><span data-stu-id="65855-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="65855-109">GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="65855-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="65855-110">Získá ukazatel rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , která představuje seznam sestavení, které hostitele očekává CLR pro načtení.</span><span class="sxs-lookup"><span data-stu-id="65855-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65855-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65855-111">Remarks</span></span>  
 <span data-ttu-id="65855-112">Hostitel není nutné implementovat `IHostAssemblyManager` nebo `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="65855-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="65855-113">Pokud se hostitel implementovat `IHostAssemblyManager`, musíte také implementovat `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="65855-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="65855-114">Modul runtime dotáže `IHostAssemblyManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="65855-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65855-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65855-115">Requirements</span></span>  
 <span data-ttu-id="65855-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65855-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65855-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65855-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65855-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65855-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65855-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65855-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65855-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65855-120">See also</span></span>

- [<span data-ttu-id="65855-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65855-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="65855-122">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65855-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="65855-123">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65855-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="65855-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="65855-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
