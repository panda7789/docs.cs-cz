---
title: ICLRHostBindingPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98a2978b440e0e72b3b4c1ac3065fbaf5d70e508
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666095"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="63871-102">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63871-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="63871-103">Poskytuje metody pro hostitele k vyhodnocení aktuální zásady vazeb a Oznamovat změny zásad pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="63871-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63871-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63871-104">Methods</span></span>  
  
|<span data-ttu-id="63871-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63871-105">Method</span></span>|<span data-ttu-id="63871-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63871-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63871-107">EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="63871-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="63871-108">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="63871-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="63871-109">ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="63871-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="63871-110">Změní zásady vazeb pro zadané sestavení a vytvoří se nová verze zásad.</span><span class="sxs-lookup"><span data-stu-id="63871-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63871-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63871-111">Requirements</span></span>  
 <span data-ttu-id="63871-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63871-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63871-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63871-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63871-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63871-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63871-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63871-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63871-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63871-116">See also</span></span>
- [<span data-ttu-id="63871-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63871-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="63871-118">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63871-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="63871-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="63871-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
