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
ms.openlocfilehash: 26de2ebf1364981d8b8f1fb38c8fa1045191114f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126629"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="7c7c2-102">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c7c2-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="7c7c2-103">Poskytuje metody, které podporují komunikaci mezi hostitelem a modulem CLR (Common Language Runtime) o sestaveních.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c7c2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c7c2-104">Methods</span></span>  
  
|<span data-ttu-id="7c7c2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-105">Method</span></span>|<span data-ttu-id="7c7c2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7c7c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c7c2-107">GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-107">GetBindingIdentityFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="7c7c2-108">Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="7c7c2-109">GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-109">GetBindingIdentityFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="7c7c2-110">Získá kanonická data identity sestavení pro sestavení v zadaném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="7c7c2-111">GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="7c7c2-112">Načte instanci [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) ze zadaného seznamu částečných identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-112">Gets an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="7c7c2-113">GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="7c7c2-114">Získá enumerátor [ICLRProbingAssemblyEnum –](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) pro identity sestavení odkazované sestavením se zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-114">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="7c7c2-115">GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="7c7c2-116">Získá instanci [ICLRReferenceAssemblyEnum –](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) , která obsahuje seznam sestavení, na která odkazuje sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-116">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="7c7c2-117">GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-117">GetReferencedAssembliesFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="7c7c2-118">Získá ukazatel na objekt `ICLRReferenceAssemblyEnum`, který obsahuje data identity sestavení pro sestavení, na která odkazuje sestavení v zadaném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="7c7c2-119">IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="7c7c2-119">IsStronglyNamed Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="7c7c2-120">Získá hodnotu, která označuje, zda je zadané sestavení silně pojmenované.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c7c2-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c7c2-121">Remarks</span></span>  
 <span data-ttu-id="7c7c2-122">Pomocí `ICLRAssemblyIdentityManager` získat instance `ICLRAssemblyReferenceList` a vytvořit výčet identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="7c7c2-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c7c2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c7c2-123">Requirements</span></span>  
 <span data-ttu-id="7c7c2-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c7c2-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c7c2-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c7c2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c7c2-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7c7c2-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c7c2-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c7c2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7c2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c7c2-128">See also</span></span>

- [<span data-ttu-id="7c7c2-129">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c7c2-129">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7c7c2-130">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c7c2-130">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="7c7c2-131">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7c7c2-131">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
