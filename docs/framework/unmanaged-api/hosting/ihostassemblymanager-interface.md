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
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501586"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="933bc-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="933bc-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="933bc-103">Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR (Common Language Runtime) nebo hostitelem.</span><span class="sxs-lookup"><span data-stu-id="933bc-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="933bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="933bc-104">Methods</span></span>  
  
|<span data-ttu-id="933bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="933bc-105">Method</span></span>|<span data-ttu-id="933bc-106">Description</span><span class="sxs-lookup"><span data-stu-id="933bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="933bc-107">GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="933bc-107">GetAssemblyStore Method</span></span>](ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="933bc-108">Získá ukazatel rozhraní na [IHostAssemblyStore](ihostassemblystore-interface.md) , který představuje seznam sestavení načtených hostitelem.</span><span class="sxs-lookup"><span data-stu-id="933bc-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="933bc-109">GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="933bc-109">GetNonHostStoreAssemblies Method</span></span>](ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="933bc-110">Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení CLR.</span><span class="sxs-lookup"><span data-stu-id="933bc-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="933bc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="933bc-111">Remarks</span></span>  
 <span data-ttu-id="933bc-112">Hostitel není vyžadován k implementaci `IHostAssemblyManager` nebo `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="933bc-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="933bc-113">Pokud hostitel implementuje `IHostAssemblyManager` , musí také implementovat `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="933bc-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="933bc-114">Běhové dotazy pro `IHostAssemblyManager` volání metody [IHostControl:: GetHostManager –](ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="933bc-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933bc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="933bc-115">Requirements</span></span>  
 <span data-ttu-id="933bc-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933bc-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933bc-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="933bc-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="933bc-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="933bc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="933bc-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933bc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933bc-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="933bc-120">See also</span></span>

- [<span data-ttu-id="933bc-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="933bc-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="933bc-122">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="933bc-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="933bc-123">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="933bc-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="933bc-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="933bc-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
