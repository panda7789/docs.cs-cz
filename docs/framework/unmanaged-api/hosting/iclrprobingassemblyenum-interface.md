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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118345f246de3d7ee68d51cf37e8cdea9de1fdba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638525"
---
# <a name="iclrprobingassemblyenum-interface"></a><span data-ttu-id="0a5c9-102">ICLRProbingAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a5c9-102">ICLRProbingAssemblyEnum Interface</span></span>
<span data-ttu-id="0a5c9-103">Poskytuje metody, které umožní získat zkušební identity sestavení s použitím identity informací o sestavení, který je interní common language runtime (CLR), aniž by bylo nutné vytvořit nebo pochopit tuto identitu hostitele.</span><span class="sxs-lookup"><span data-stu-id="0a5c9-103">Provides methods that enable the host to get the probing identities of an assembly by using the assembly's identity information that is internal to the common language runtime (CLR), without needing to create or understand that identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a5c9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a5c9-104">Methods</span></span>  
  
|<span data-ttu-id="0a5c9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a5c9-105">Method</span></span>|<span data-ttu-id="0a5c9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a5c9-107">Get – metoda</span><span class="sxs-lookup"><span data-stu-id="0a5c9-107">Get Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|<span data-ttu-id="0a5c9-108">Získá identitu sestavení v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="0a5c9-108">Gets the assembly identity at the specified index.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a5c9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a5c9-109">Remarks</span></span>  
 <span data-ttu-id="0a5c9-110">Metody jako [iclrassemblyidentitymanager::getprobingassembliesfromreference –](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) vrátit `ICLRProbingAssemblyEnum` instance.</span><span class="sxs-lookup"><span data-stu-id="0a5c9-110">Methods such as [ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) return an `ICLRProbingAssemblyEnum` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a5c9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a5c9-111">Requirements</span></span>  
 <span data-ttu-id="0a5c9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a5c9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a5c9-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a5c9-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a5c9-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a5c9-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a5c9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a5c9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5c9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a5c9-116">See also</span></span>

- [<span data-ttu-id="0a5c9-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a5c9-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0a5c9-118">ICLRAssemblyReferenceList – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a5c9-118">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0a5c9-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0a5c9-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
