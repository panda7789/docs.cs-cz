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
ms.openlocfilehash: 8106dd70f6c4099b2246530622f0845f22a0c53f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805042"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="4515f-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4515f-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="4515f-103">Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR (Common Language Runtime) nebo hostitelem.</span><span class="sxs-lookup"><span data-stu-id="4515f-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4515f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4515f-104">Methods</span></span>  
  
|<span data-ttu-id="4515f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4515f-105">Method</span></span>|<span data-ttu-id="4515f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4515f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4515f-107">GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="4515f-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="4515f-108">Získá ukazatel rozhraní na [IHostAssemblyStore](ihostassemblystore-interface.md) , který představuje seznam sestavení načtených hostitelem.</span><span class="sxs-lookup"><span data-stu-id="4515f-108">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="4515f-109">GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="4515f-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="4515f-110">Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení CLR.</span><span class="sxs-lookup"><span data-stu-id="4515f-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4515f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4515f-111">Remarks</span></span>  
 <span data-ttu-id="4515f-112">Hostitel není vyžadován k implementaci `IHostAssemblyManager` nebo `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="4515f-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="4515f-113">Pokud hostitel implementuje `IHostAssemblyManager` , musí také implementovat `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="4515f-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="4515f-114">Běhové dotazy pro `IHostAssemblyManager` volání metody [IHostControl:: GetHostManager –](ihostcontrol-gethostmanager-method.md) při inicializaci s `IID` IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="4515f-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4515f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4515f-115">Requirements</span></span>  
 <span data-ttu-id="4515f-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4515f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4515f-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4515f-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4515f-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4515f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4515f-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4515f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4515f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4515f-120">See also</span></span>

- [<span data-ttu-id="4515f-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4515f-121">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4515f-122">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4515f-122">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="4515f-123">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4515f-123">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="4515f-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4515f-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
