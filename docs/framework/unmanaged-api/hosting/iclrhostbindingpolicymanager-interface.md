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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074193"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="493d4-102">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="493d4-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="493d4-103">Poskytuje metody pro hostitele k vyhodnocení aktuální zásady vazeb a Oznamovat změny zásad pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="493d4-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="493d4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="493d4-104">Methods</span></span>  
  
|<span data-ttu-id="493d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="493d4-105">Method</span></span>|<span data-ttu-id="493d4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="493d4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="493d4-107">EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="493d4-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="493d4-108">Vyhodnotí zásady vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="493d4-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="493d4-109">ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="493d4-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="493d4-110">Změní zásady vazeb pro zadané sestavení a vytvoří se nová verze zásad.</span><span class="sxs-lookup"><span data-stu-id="493d4-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="493d4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="493d4-111">Requirements</span></span>  
 <span data-ttu-id="493d4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="493d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493d4-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="493d4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="493d4-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="493d4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="493d4-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493d4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493d4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="493d4-116">See also</span></span>

- [<span data-ttu-id="493d4-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="493d4-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="493d4-118">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="493d4-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="493d4-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="493d4-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
