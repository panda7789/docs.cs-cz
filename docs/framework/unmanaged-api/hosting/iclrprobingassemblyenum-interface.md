---
title: ICLRProbingAssemblyEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
ms.openlocfilehash: e1459c1604f3f8f043fd9b61533235ab7861c910
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120565"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="b65af-102">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b65af-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="b65af-103">Poskytuje metody, které umožňují hostiteli získat identity sestavení pomocí informací o identitě sestavení, které jsou interní pro modul CLR (Common Language Runtime), a to bez nutnosti vytvořit nebo porozumět této identitě.</span><span class="sxs-lookup"><span data-stu-id="b65af-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b65af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b65af-104">Methods</span></span>  
  
|<span data-ttu-id="b65af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b65af-105">Method</span></span>|<span data-ttu-id="b65af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b65af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b65af-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="b65af-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="b65af-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="b65af-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b65af-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b65af-109">Remarks</span></span>  
 <span data-ttu-id="b65af-110">Metody jako [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vracejí instanci `ICLRProbingAssemblyEnum`.</span><span class="sxs-lookup"><span data-stu-id="b65af-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b65af-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b65af-111">Requirements</span></span>  
 <span data-ttu-id="b65af-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b65af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b65af-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b65af-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b65af-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b65af-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b65af-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b65af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b65af-116">See also</span></span>

- [<span data-ttu-id="b65af-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b65af-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="b65af-118">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b65af-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="b65af-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b65af-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
