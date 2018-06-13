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
ms.openlocfilehash: c8c8d17723481fc5b41fe5f3006fe8db2c53d1ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438477"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="d7a7b-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7a7b-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="d7a7b-103">Poskytuje metody, které umožňují hostitele k určení sady sestavení, které se mají načíst modul CLR (CLR), nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7a7b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d7a7b-104">Methods</span></span>  
  
|<span data-ttu-id="d7a7b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7a7b-105">Method</span></span>|<span data-ttu-id="d7a7b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d7a7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7a7b-107">GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="d7a7b-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="d7a7b-108">Získá ukazatele rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení načíst pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="d7a7b-109">GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="d7a7b-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="d7a7b-110">Získá ukazatele rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , která představuje seznam sestavení, které hostitel očekává CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7a7b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7a7b-111">Remarks</span></span>  
 <span data-ttu-id="d7a7b-112">Hostitel není potřeba implementovat `IHostAssemblyManager` nebo `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="d7a7b-113">Pokud hostitel implementovat `IHostAssemblyManager`, musíte také implementovat `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="d7a7b-114">Modul runtime dotazuje na `IHostAssemblyManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="d7a7b-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a7b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7a7b-115">Requirements</span></span>  
 <span data-ttu-id="d7a7b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a7b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a7b-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d7a7b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7a7b-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d7a7b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7a7b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a7b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a7b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7a7b-120">See Also</span></span>  
 [<span data-ttu-id="d7a7b-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7a7b-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="d7a7b-122">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7a7b-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="d7a7b-123">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7a7b-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="d7a7b-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d7a7b-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
