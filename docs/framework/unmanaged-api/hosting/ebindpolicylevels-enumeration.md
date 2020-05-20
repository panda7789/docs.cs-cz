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
ms.openlocfilehash: 94d2ec12309249afbecdc4130f8fe20c927b0a9b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616369"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="81ca0-102">EBindPolicyLevels – výčet</span><span class="sxs-lookup"><span data-stu-id="81ca0-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="81ca0-103">Poskytuje příznaky pro určení úrovně, na které se má použít nebo upravit zásady sestavení.</span><span class="sxs-lookup"><span data-stu-id="81ca0-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ca0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81ca0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="81ca0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="81ca0-105">Members</span></span>  
  
|<span data-ttu-id="81ca0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="81ca0-106">Member</span></span>|<span data-ttu-id="81ca0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="81ca0-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="81ca0-108">Určuje, že zásada by se měla použít na úrovni správce.</span><span class="sxs-lookup"><span data-stu-id="81ca0-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="81ca0-109">Určuje, že zásada by se měla použít na úrovni aplikace.</span><span class="sxs-lookup"><span data-stu-id="81ca0-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="81ca0-110">Určuje, že zásada by se měla použít na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="81ca0-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="81ca0-111">Neurčuje žádné příznaky na úrovni zásad.</span><span class="sxs-lookup"><span data-stu-id="81ca0-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="81ca0-112">Určuje, že zásada by se měla použít na úrovni vydavatele.</span><span class="sxs-lookup"><span data-stu-id="81ca0-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="81ca0-113">Určuje, že zásada by se měla použít na proměnlivých úrovních.</span><span class="sxs-lookup"><span data-stu-id="81ca0-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="81ca0-114">Určuje, že zásady by měly podporovat přenositelnost mezi implementacemi .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="81ca0-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="81ca0-115">Viz prvek [ \< značka supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="81ca0-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="81ca0-116">Určuje, že zásady by měly být sjednoceny s modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="81ca0-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81ca0-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81ca0-117">Remarks</span></span>  
 <span data-ttu-id="81ca0-118">Tento výčet je předán metodám rozhraní [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) k určení změn v zásadách použití.</span><span class="sxs-lookup"><span data-stu-id="81ca0-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ca0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81ca0-119">Requirements</span></span>  
 <span data-ttu-id="81ca0-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ca0-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ca0-121">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="81ca0-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81ca0-122">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="81ca0-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81ca0-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ca0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ca0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="81ca0-124">See also</span></span>

- [<span data-ttu-id="81ca0-125">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81ca0-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="81ca0-126">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="81ca0-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
