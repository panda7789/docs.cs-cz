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
ms.openlocfilehash: 9ed317a451e6e35aeac3bc1b83f78d1400ea5c07
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136431"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="a1814-102">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1814-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="a1814-103">Poskytuje metody pro hostitele k vyhodnocení aktuálních zásad vazby a oznamování změn zásad pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="a1814-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1814-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1814-104">Methods</span></span>  
  
|<span data-ttu-id="a1814-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1814-105">Method</span></span>|<span data-ttu-id="a1814-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1814-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1814-107">EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="a1814-107">EvaluatePolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="a1814-108">Vyhodnotí zásady vytváření vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="a1814-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="a1814-109">ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="a1814-109">ModifyApplicationPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="a1814-110">Upraví zásadu vazby pro zadané sestavení a vytvoří novou verzi zásad.</span><span class="sxs-lookup"><span data-stu-id="a1814-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1814-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1814-111">Requirements</span></span>  
 <span data-ttu-id="a1814-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1814-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1814-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1814-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1814-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1814-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1814-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1814-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1814-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1814-116">See also</span></span>

- [<span data-ttu-id="a1814-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1814-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a1814-118">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1814-118">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [<span data-ttu-id="a1814-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a1814-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
