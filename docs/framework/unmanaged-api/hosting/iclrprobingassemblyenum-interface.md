---
title: "ICLRProbingAssemblyEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRProbingAssemblyEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRProbingAssemblyEnum
helpviewer_keywords: ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31f3bfcb2b70bda952f0e4bb43dd8b0067e6ef1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="b3aa5-102">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3aa5-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="b3aa5-103">Poskytuje metody, které umožňují získat zkušební identity sestavení pomocí informace identity je sestavení, která je interní modul CLR (CLR), aniž by museli vytvářet nebo pochopit tuto identitu hostitele.</span><span class="sxs-lookup"><span data-stu-id="b3aa5-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3aa5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b3aa5-104">Methods</span></span>  
  
|<span data-ttu-id="b3aa5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3aa5-105">Method</span></span>|<span data-ttu-id="b3aa5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b3aa5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3aa5-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="b3aa5-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="b3aa5-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="b3aa5-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3aa5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3aa5-109">Remarks</span></span>  
 <span data-ttu-id="b3aa5-110">Metody, jako [iclrassemblyidentitymanager::getprobingassembliesfromreference –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vrátit `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="b3aa5-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3aa5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3aa5-111">Requirements</span></span>  
 <span data-ttu-id="b3aa5-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3aa5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3aa5-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b3aa5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3aa5-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3aa5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3aa5-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3aa5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3aa5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3aa5-116">See Also</span></span>  
 [<span data-ttu-id="b3aa5-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3aa5-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b3aa5-118">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3aa5-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="b3aa5-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b3aa5-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
