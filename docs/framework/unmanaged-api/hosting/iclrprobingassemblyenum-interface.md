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
ms.openlocfilehash: e1e114070f39e75254fc1bc0f8c1bf3e4733d5a2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703374"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="5a8d8-102">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a8d8-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="5a8d8-103">Poskytuje metody, které umožňují hostiteli získat identity sestavení pomocí informací o identitě sestavení, které jsou interní pro modul CLR (Common Language Runtime), a to bez nutnosti vytvořit nebo porozumět této identitě.</span><span class="sxs-lookup"><span data-stu-id="5a8d8-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a8d8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a8d8-104">Methods</span></span>  
  
|<span data-ttu-id="5a8d8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a8d8-105">Method</span></span>|<span data-ttu-id="5a8d8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5a8d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a8d8-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="5a8d8-107">Get Method</span></span>](iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="5a8d8-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="5a8d8-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a8d8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a8d8-109">Remarks</span></span>  
 <span data-ttu-id="5a8d8-110">Metody jako [ICLRAssemblyIdentityManager:: GetProbingAssembliesFromReference –](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vrátí `ICLRProbingAssemblyEnum` instanci.</span><span class="sxs-lookup"><span data-stu-id="5a8d8-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a8d8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a8d8-111">Requirements</span></span>  
 <span data-ttu-id="5a8d8-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a8d8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a8d8-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5a8d8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a8d8-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5a8d8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a8d8-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a8d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8d8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a8d8-116">See also</span></span>

- [<span data-ttu-id="5a8d8-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a8d8-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5a8d8-118">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a8d8-118">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="5a8d8-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5a8d8-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
