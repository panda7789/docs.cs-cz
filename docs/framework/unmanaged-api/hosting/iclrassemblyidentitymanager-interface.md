---
title: ICLRAssemblyIdentityManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209798"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="d2027-102">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2027-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="d2027-103">Poskytuje metody, které podporují komunikaci mezi hostiteli a common language runtime (CLR) o sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2027-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d2027-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d2027-104">Methods</span></span>  
  
|<span data-ttu-id="d2027-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-105">Method</span></span>|<span data-ttu-id="d2027-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d2027-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d2027-107">GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="d2027-108">Získá identitu sestavení, vytvoření vazby mezi daty pro sestavení v zadané cesty k souboru.</span><span class="sxs-lookup"><span data-stu-id="d2027-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="d2027-109">GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="d2027-110">Získá data identit canonical sestavení pro sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2027-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="d2027-111">GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="d2027-112">Získá [iclrassemblyreferencelist –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance ze zadaného seznamu identit částečného sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2027-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="d2027-113">GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="d2027-114">Získá [iclrprobingassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerátor pro identity sestavení odkazuje sestavení se zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="d2027-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="d2027-115">GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="d2027-116">Získá [iclrreferenceassemblyenum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance, která obsahuje seznam sestavení odkazovaných sestavení v cestě zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d2027-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="d2027-117">GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="d2027-118">Získá ukazatel `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identity sestavení pro sestavení odkazuje na sestavení v zadaného datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d2027-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="d2027-119">IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="d2027-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="d2027-120">Získá hodnotu určující, zda je zadané sestavení silný název.</span><span class="sxs-lookup"><span data-stu-id="d2027-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2027-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2027-121">Remarks</span></span>  
 <span data-ttu-id="d2027-122">Použití `ICLRAssemblyIdentityManager` získat instance `ICLRAssemblyReferenceList` a k vyčíslení identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="d2027-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2027-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2027-123">Requirements</span></span>  
 <span data-ttu-id="d2027-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2027-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2027-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2027-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2027-126">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2027-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d2027-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d2027-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2027-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2027-128">See also</span></span>

- [<span data-ttu-id="d2027-129">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2027-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="d2027-130">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2027-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="d2027-131">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="d2027-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
