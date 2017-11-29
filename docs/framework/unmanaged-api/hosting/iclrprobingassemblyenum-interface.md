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
ms.openlocfilehash: 6d810ab6e62c6df1b00305947de552ecdbe82141
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="3a623-102">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a623-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="3a623-103">Poskytuje metody, které umožňují získat zkušební identity sestavení pomocí informace identity je sestavení, která je interní modul CLR (CLR), aniž by museli vytvářet nebo pochopit tuto identitu hostitele.</span><span class="sxs-lookup"><span data-stu-id="3a623-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a623-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3a623-104">Methods</span></span>  
  
|<span data-ttu-id="3a623-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a623-105">Method</span></span>|<span data-ttu-id="3a623-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3a623-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a623-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="3a623-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="3a623-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="3a623-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a623-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a623-109">Remarks</span></span>  
 <span data-ttu-id="3a623-110">Metody, jako [iclrassemblyidentitymanager::getprobingassembliesfromreference –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vrátit `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="3a623-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a623-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a623-111">Requirements</span></span>  
 <span data-ttu-id="3a623-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a623-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a623-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a623-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a623-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a623-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a623-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a623-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a623-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a623-116">See Also</span></span>  
 [<span data-ttu-id="3a623-117">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a623-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="3a623-118">Iclrassemblyreferencelist – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a623-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="3a623-119">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="3a623-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
