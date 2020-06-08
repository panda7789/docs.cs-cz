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
ms.openlocfilehash: 3611de471001d31c40984e71d49ce376bb3e4607
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504287"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="a579c-102">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a579c-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="a579c-103">Poskytuje metody, které podporují komunikaci mezi hostitelem a modulem CLR (Common Language Runtime) o sestaveních.</span><span class="sxs-lookup"><span data-stu-id="a579c-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a579c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a579c-104">Methods</span></span>  
  
|<span data-ttu-id="a579c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-105">Method</span></span>|<span data-ttu-id="a579c-106">Description</span><span class="sxs-lookup"><span data-stu-id="a579c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a579c-107">GetBindingIdentityFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="a579c-108">Získá datovou vazbu identity sestavení pro sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="a579c-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="a579c-109">GetBindingIdentityFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="a579c-110">Získá kanonická data identity sestavení pro sestavení v zadaném datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="a579c-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="a579c-111">GetCLRAssemblyReferenceList – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-111">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="a579c-112">Načte instanci [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) ze zadaného seznamu částečných identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="a579c-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="a579c-113">GetProbingAssembliesFromReference – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-113">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="a579c-114">Získá enumerátor [ICLRProbingAssemblyEnum –](iclrprobingassemblyenum-interface.md) pro identity sestavení odkazované sestavením se zadanou identitou.</span><span class="sxs-lookup"><span data-stu-id="a579c-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="a579c-115">GetReferencedAssembliesFromFile – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-115">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="a579c-116">Získá instanci [ICLRReferenceAssemblyEnum –](iclrreferenceassemblyenum-interface.md) , která obsahuje seznam sestavení, na která odkazuje sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="a579c-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="a579c-117">GetReferencedAssembliesFromStream – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="a579c-118">Získá ukazatel na `ICLRReferenceAssemblyEnum` objekt, který obsahuje data identity sestavení pro sestavení, na která odkazuje sestavení v zadaném proudu.</span><span class="sxs-lookup"><span data-stu-id="a579c-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="a579c-119">IsStronglyNamed – metoda</span><span class="sxs-lookup"><span data-stu-id="a579c-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="a579c-120">Získá hodnotu, která označuje, zda je zadané sestavení silně pojmenované.</span><span class="sxs-lookup"><span data-stu-id="a579c-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a579c-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a579c-121">Remarks</span></span>  
 <span data-ttu-id="a579c-122">Slouží `ICLRAssemblyIdentityManager` k získání instancí `ICLRAssemblyReferenceList` a k zobrazení výčtu identit sestavení.</span><span class="sxs-lookup"><span data-stu-id="a579c-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a579c-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a579c-123">Requirements</span></span>  
 <span data-ttu-id="a579c-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a579c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a579c-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a579c-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a579c-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a579c-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a579c-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a579c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a579c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a579c-128">See also</span></span>

- [<span data-ttu-id="a579c-129">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a579c-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a579c-130">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a579c-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="a579c-131">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a579c-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
