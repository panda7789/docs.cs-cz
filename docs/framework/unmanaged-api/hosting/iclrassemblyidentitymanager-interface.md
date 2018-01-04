---
title: "ICLRAssemblyIdentityManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager
helpviewer_keywords: ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 168c67eb701d7dfc461553cfe32ed43dcea5e844
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="b19b1-102">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b19b1-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="b19b1-103">Poskytuje metody, které podporují komunikaci mezi hostitelem a common language runtime (CLR) o sestavení.</span><span class="sxs-lookup"><span data-stu-id="b19b1-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b19b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b19b1-104">Methods</span></span>  
  
|<span data-ttu-id="b19b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-105">Method</span></span>|<span data-ttu-id="b19b1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b19b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b19b1-107">GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="b19b1-108">Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="b19b1-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="b19b1-109">GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="b19b1-110">Získá data identit kanonický sestavení pro sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="b19b1-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="b19b1-111">GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="b19b1-112">Získá [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instanci ze seznamu zadaný částečného sestavení identit.</span><span class="sxs-lookup"><span data-stu-id="b19b1-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="b19b1-113">GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="b19b1-114">Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení se zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="b19b1-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="b19b1-115">GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="b19b1-116">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instanci, která obsahuje seznam sestavení odkazuje sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="b19b1-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="b19b1-117">GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="b19b1-118">Získá odkazy `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="b19b1-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="b19b1-119">IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="b19b1-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="b19b1-120">Získá hodnotu, která určuje, zda zadané sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="b19b1-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b19b1-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b19b1-121">Remarks</span></span>  
 <span data-ttu-id="b19b1-122">Použití `ICLRAssemblyIdentityManager` získat instancí `ICLRAssemblyReferenceList` a chcete získat výčet identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="b19b1-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b19b1-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b19b1-123">Requirements</span></span>  
 <span data-ttu-id="b19b1-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b19b1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b19b1-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b19b1-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b19b1-126">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b19b1-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b19b1-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b19b1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19b1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b19b1-128">See Also</span></span>  
 [<span data-ttu-id="b19b1-129">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b19b1-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b19b1-130">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b19b1-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="b19b1-131">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b19b1-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
