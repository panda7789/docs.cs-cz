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
ms.openlocfilehash: e494bbbd08a77329b7b64816216e4bb2e1b724a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074193"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="5642b-102">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5642b-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="5642b-103">Poskytuje metody pro hostitele k vyhodnocení aktuální zásady vazeb a Oznamovat změny zásad pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="5642b-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5642b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5642b-104">Methods</span></span>  
  
|<span data-ttu-id="5642b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5642b-105">Method</span></span>|<span data-ttu-id="5642b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5642b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5642b-107">EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="5642b-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="5642b-108">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="5642b-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="5642b-109">ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="5642b-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="5642b-110">Změní zásady vazeb pro zadané sestavení a vytvoří se nová verze zásad.</span><span class="sxs-lookup"><span data-stu-id="5642b-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5642b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5642b-111">Requirements</span></span>  
 <span data-ttu-id="5642b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5642b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5642b-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5642b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5642b-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5642b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5642b-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5642b-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5642b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5642b-116">See also</span></span>

- [<span data-ttu-id="5642b-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5642b-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5642b-118">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5642b-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="5642b-119">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="5642b-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
