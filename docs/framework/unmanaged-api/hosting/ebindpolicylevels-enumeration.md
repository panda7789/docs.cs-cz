---
title: EBindPolicyLevels – výčet
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769756"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="296da-102">EBindPolicyLevels – výčet</span><span class="sxs-lookup"><span data-stu-id="296da-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="296da-103">Poskytuje příznaků, které určují úroveň, kde nastavení nebo změna zásady sestavení.</span><span class="sxs-lookup"><span data-stu-id="296da-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="296da-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="296da-105">Členové</span><span class="sxs-lookup"><span data-stu-id="296da-105">Members</span></span>  
  
|<span data-ttu-id="296da-106">Člen</span><span class="sxs-lookup"><span data-stu-id="296da-106">Member</span></span>|<span data-ttu-id="296da-107">Popis</span><span class="sxs-lookup"><span data-stu-id="296da-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="296da-108">Určuje, že je použita zásada na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="296da-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="296da-109">Určuje, že je použita zásada na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="296da-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="296da-110">Určuje, že je použita zásada na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="296da-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="296da-111">Určuje příznaky žádná úroveň zásad.</span><span class="sxs-lookup"><span data-stu-id="296da-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="296da-112">Určuje, že je použita zásada na úrovni vydavatele.</span><span class="sxs-lookup"><span data-stu-id="296da-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="296da-113">Určuje, že zásada by měla být použít proměnné na úrovni.</span><span class="sxs-lookup"><span data-stu-id="296da-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="296da-114">Určuje, že zásady by měly podporovat přenositelnost mezi implementacemi sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="296da-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="296da-115">Zobrazit [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) prvek souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="296da-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="296da-116">Určuje, že zásady by měl unified, který modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="296da-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="296da-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="296da-117">Remarks</span></span>  
 <span data-ttu-id="296da-118">Tento výčet je předán do metody [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) rozhraní a zadejte změny v zásadách aplikací.</span><span class="sxs-lookup"><span data-stu-id="296da-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296da-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="296da-119">Requirements</span></span>  
 <span data-ttu-id="296da-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="296da-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="296da-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="296da-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="296da-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="296da-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="296da-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="296da-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296da-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="296da-124">See also</span></span>

- [<span data-ttu-id="296da-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="296da-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="296da-126">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="296da-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
