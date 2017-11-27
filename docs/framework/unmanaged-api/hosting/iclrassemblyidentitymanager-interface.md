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
ms.openlocfilehash: 8d7fe632941c4cf0c20841ece390d2f41f28337d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="6f8f2-102">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f8f2-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="6f8f2-103">Poskytuje metody, které podporují komunikaci mezi hostitelem a common language runtime (CLR) o sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f8f2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6f8f2-104">Methods</span></span>  
  
|<span data-ttu-id="6f8f2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-105">Method</span></span>|<span data-ttu-id="6f8f2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6f8f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f8f2-107">Getbindingidentityfromfile – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="6f8f2-108">Získá identitu sestavení vazba dat pro sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="6f8f2-109">Getbindingidentityfromstream – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="6f8f2-110">Získá data identit kanonický sestavení pro sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="6f8f2-111">Getclrassemblyreferencelist – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="6f8f2-112">Získá [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instanci ze seznamu zadaný částečného sestavení identit.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="6f8f2-113">Getprobingassembliesfromreference – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="6f8f2-114">Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení se zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="6f8f2-115">Getreferencedassembliesfromfile – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="6f8f2-116">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instanci, která obsahuje seznam sestavení odkazuje sestavení v zadaná cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="6f8f2-117">Getreferencedassembliesfromstream – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="6f8f2-118">Získá odkazy `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identit sestavení pro sestavení odkazuje sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="6f8f2-119">Isstronglynamed – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8f2-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="6f8f2-120">Získá hodnotu, která určuje, zda zadané sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f8f2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f8f2-121">Remarks</span></span>  
 <span data-ttu-id="6f8f2-122">Použití `ICLRAssemblyIdentityManager` získat instancí `ICLRAssemblyReferenceList` a chcete získat výčet identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="6f8f2-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f8f2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f8f2-123">Requirements</span></span>  
 <span data-ttu-id="6f8f2-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f8f2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f8f2-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6f8f2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6f8f2-126">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f8f2-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f8f2-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f8f2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f8f2-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f8f2-128">See Also</span></span>  
 [<span data-ttu-id="6f8f2-129">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f8f2-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="6f8f2-130">Iclrprobingassemblyenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f8f2-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [<span data-ttu-id="6f8f2-131">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="6f8f2-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
