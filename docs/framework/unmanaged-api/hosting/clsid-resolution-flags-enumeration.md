---
title: "CLSID_RESOLUTION_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 840e3c3c155a383f94051940b6d63dea3412bf63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="0d37a-102">CLSID_RESOLUTION_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="0d37a-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="0d37a-103">Obsahuje hodnoty, které označují, jak by měla vyřešit common language runtime (CLR) `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="0d37a-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d37a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d37a-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0d37a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0d37a-105">Members</span></span>  
  
|<span data-ttu-id="0d37a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0d37a-106">Member</span></span>|<span data-ttu-id="0d37a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0d37a-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="0d37a-108">Určuje výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="0d37a-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="0d37a-109">Označuje, že modul runtime vyhledá registru a platí shim zásad.</span><span class="sxs-lookup"><span data-stu-id="0d37a-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d37a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d37a-110">Requirements</span></span>  
 <span data-ttu-id="0d37a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d37a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d37a-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d37a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d37a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d37a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d37a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d37a-114">See Also</span></span>  
 [<span data-ttu-id="0d37a-115">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="0d37a-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
