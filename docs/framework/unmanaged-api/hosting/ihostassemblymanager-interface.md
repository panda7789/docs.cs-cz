---
title: "IHostAssemblyManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b3761063201a48303884fdecddddf02558cd4e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="25df5-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25df5-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="25df5-103">Poskytuje metody, které umožňují hostitele k určení sady sestavení, které se mají načíst modul CLR (CLR), nebo hostitele.</span><span class="sxs-lookup"><span data-stu-id="25df5-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25df5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="25df5-104">Methods</span></span>  
  
|<span data-ttu-id="25df5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="25df5-105">Method</span></span>|<span data-ttu-id="25df5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="25df5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25df5-107">Getassemblystore – metoda</span><span class="sxs-lookup"><span data-stu-id="25df5-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="25df5-108">Získá ukazatele rozhraní k [ihostassemblystore –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , která představuje seznam sestavení načíst pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="25df5-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="25df5-109">Getnonhoststoreassemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="25df5-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="25df5-110">Získá ukazatele rozhraní k [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , která představuje seznam sestavení, které hostitel očekává CLR načíst.</span><span class="sxs-lookup"><span data-stu-id="25df5-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25df5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25df5-111">Remarks</span></span>  
 <span data-ttu-id="25df5-112">Hostitel není potřeba implementovat `IHostAssemblyManager` nebo `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="25df5-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="25df5-113">Pokud hostitel implementovat `IHostAssemblyManager`, musíte také implementovat `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="25df5-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="25df5-114">Modul runtime dotazuje na `IHostAssemblyManager` voláním [ihostcontrol::gethostmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` z IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="25df5-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25df5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25df5-115">Requirements</span></span>  
 <span data-ttu-id="25df5-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25df5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25df5-117">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25df5-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25df5-118">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25df5-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25df5-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25df5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25df5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="25df5-120">See Also</span></span>  
 [<span data-ttu-id="25df5-121">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25df5-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="25df5-122">Ihostassemblystore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25df5-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [<span data-ttu-id="25df5-123">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25df5-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="25df5-124">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="25df5-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
