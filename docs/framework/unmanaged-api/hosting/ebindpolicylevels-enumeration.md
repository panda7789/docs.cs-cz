---
title: "EBindPolicyLevels – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EBindPolicyLevels
api_location: mscoree.dll
api_type: COM
f1_keywords: EBindPolicyLevels
helpviewer_keywords: EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e55fdb58129cd530bb63f26fab0be471b133d62f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="801a9-102">EBindPolicyLevels – výčet</span><span class="sxs-lookup"><span data-stu-id="801a9-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="801a9-103">Poskytuje příznaky k určení úrovně, kdy má nastavení nebo změna zásad sestavení.</span><span class="sxs-lookup"><span data-stu-id="801a9-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="801a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="801a9-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="801a9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="801a9-105">Members</span></span>  
  
|<span data-ttu-id="801a9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="801a9-106">Member</span></span>|<span data-ttu-id="801a9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="801a9-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="801a9-108">Určuje, že by měl být zásada na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="801a9-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="801a9-109">Určuje, že by měl být zásada na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="801a9-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="801a9-110">Určuje, že by měl být zásada na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="801a9-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="801a9-111">Určuje příznaky žádné zásady úrovni.</span><span class="sxs-lookup"><span data-stu-id="801a9-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="801a9-112">Určuje, že je použita zásada na úrovni vydavatele.</span><span class="sxs-lookup"><span data-stu-id="801a9-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="801a9-113">Určuje, že zásady by měl být použít proměnné na úrovni.</span><span class="sxs-lookup"><span data-stu-id="801a9-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="801a9-114">Určuje, že zásady by měly podporovat přenositelnost mezi implementací sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="801a9-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="801a9-115">Najdete v článku [ \<supportPortability – >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) konfigurační soubor prvek.</span><span class="sxs-lookup"><span data-stu-id="801a9-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="801a9-116">Určuje, že zásady by měl být unified na který common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="801a9-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="801a9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="801a9-117">Remarks</span></span>  
 <span data-ttu-id="801a9-118">Tento výčet je předán metody [iclrhostbindingpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) rozhraní k zadání změny v zásadách aplikací.</span><span class="sxs-lookup"><span data-stu-id="801a9-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="801a9-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="801a9-119">Requirements</span></span>  
 <span data-ttu-id="801a9-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="801a9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="801a9-121">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="801a9-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="801a9-122">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="801a9-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="801a9-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="801a9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="801a9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="801a9-124">See Also</span></span>  
 [<span data-ttu-id="801a9-125">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="801a9-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="801a9-126">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="801a9-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
