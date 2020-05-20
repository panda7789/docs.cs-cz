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
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703566"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="4b0c8-102">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b0c8-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="4b0c8-103">Poskytuje metody pro hostitele k vyhodnocení aktuálních zásad vazby a oznamování změn zásad pro zadané sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b0c8-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b0c8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4b0c8-104">Methods</span></span>  
  
|<span data-ttu-id="4b0c8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b0c8-105">Method</span></span>|<span data-ttu-id="4b0c8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4b0c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b0c8-107">EvaluatePolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="4b0c8-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="4b0c8-108">Vyhodnotí zásady vytváření vazeb jménem hostitele.</span><span class="sxs-lookup"><span data-stu-id="4b0c8-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="4b0c8-109">ModifyApplicationPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="4b0c8-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="4b0c8-110">Upraví zásadu vazby pro zadané sestavení a vytvoří novou verzi zásad.</span><span class="sxs-lookup"><span data-stu-id="4b0c8-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b0c8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b0c8-111">Requirements</span></span>  
 <span data-ttu-id="4b0c8-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b0c8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b0c8-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b0c8-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b0c8-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4b0c8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b0c8-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b0c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0c8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b0c8-116">See also</span></span>

- [<span data-ttu-id="4b0c8-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b0c8-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="4b0c8-118">IHostAssemblyStore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b0c8-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="4b0c8-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4b0c8-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
