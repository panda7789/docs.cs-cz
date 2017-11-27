---
title: "CLSID_RESOLUTION_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLSID_RESOLUTION_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: CLSID_RESOLUTION_FLAGS
helpviewer_keywords: CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17e74e8b39ff9079973063f4ea703607411ab93d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="f361f-102">CLSID_RESOLUTION_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="f361f-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="f361f-103">Obsahuje hodnoty, které označují, jak by měla vyřešit common language runtime (CLR) `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="f361f-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f361f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f361f-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="f361f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f361f-105">Members</span></span>  
  
|<span data-ttu-id="f361f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f361f-106">Member</span></span>|<span data-ttu-id="f361f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f361f-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="f361f-108">Určuje výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="f361f-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="f361f-109">Označuje, že modul runtime vyhledá registru a platí shim zásad.</span><span class="sxs-lookup"><span data-stu-id="f361f-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f361f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f361f-110">Requirements</span></span>  
 <span data-ttu-id="f361f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f361f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f361f-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f361f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f361f-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f361f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f361f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f361f-114">See Also</span></span>  
 [<span data-ttu-id="f361f-115">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="f361f-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
