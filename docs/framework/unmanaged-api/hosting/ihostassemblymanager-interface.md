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
ms.openlocfilehash: d9feeaf5f85d6f84a13e74a893b82c97fdaf023c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124511"
---
# <a name="ihostassemblymanager-interface"></a><span data-ttu-id="a1a68-102">IHostAssemblyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1a68-102">IHostAssemblyManager Interface</span></span>
<span data-ttu-id="a1a68-103">Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR (Common Language Runtime) nebo hostitelem.</span><span class="sxs-lookup"><span data-stu-id="a1a68-103">Provides methods that allow a host to specify sets of assemblies that should be loaded by the common language runtime (CLR) or by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1a68-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1a68-104">Methods</span></span>  
  
|<span data-ttu-id="a1a68-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1a68-105">Method</span></span>|<span data-ttu-id="a1a68-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1a68-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1a68-107">GetAssemblyStore – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a68-107">GetAssemblyStore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|<span data-ttu-id="a1a68-108">Získá ukazatel rozhraní na [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) , který představuje seznam sestavení načtených hostitelem.</span><span class="sxs-lookup"><span data-stu-id="a1a68-108">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>|  
|[<span data-ttu-id="a1a68-109">GetNonHostStoreAssemblies – metoda</span><span class="sxs-lookup"><span data-stu-id="a1a68-109">GetNonHostStoreAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|<span data-ttu-id="a1a68-110">Získá ukazatel rozhraní na [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , který představuje seznam sestavení, která hostitel očekává načtení CLR.</span><span class="sxs-lookup"><span data-stu-id="a1a68-110">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the CLR to load.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1a68-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1a68-111">Remarks</span></span>  
 <span data-ttu-id="a1a68-112">Hostitel není vyžadován k implementaci `IHostAssemblyManager` nebo `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="a1a68-112">The host is not required to implement `IHostAssemblyManager` or `IHostAssemblyStore`.</span></span> <span data-ttu-id="a1a68-113">Pokud hostitel implementuje `IHostAssemblyManager`, musí také implementovat `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="a1a68-113">If the host does implement `IHostAssemblyManager`, it must also implement `IHostAssemblyStore`.</span></span>  
  
 <span data-ttu-id="a1a68-114">Běhové dotazy pro `IHostAssemblyManager` voláním [IHostControl:: GetHostManager –](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) při inicializaci pomocí `IID` IID_IHostAssemblyManager.</span><span class="sxs-lookup"><span data-stu-id="a1a68-114">The runtime queries for an `IHostAssemblyManager` by calling [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) upon initialization with an `IID` of IID_IHostAssemblyManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1a68-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1a68-115">Requirements</span></span>  
 <span data-ttu-id="a1a68-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1a68-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1a68-117">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1a68-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1a68-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1a68-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1a68-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1a68-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a68-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1a68-120">See also</span></span>

- [<span data-ttu-id="a1a68-121">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1a68-121">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a1a68-122">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1a68-122">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="a1a68-123">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1a68-123">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="a1a68-124">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1a68-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
