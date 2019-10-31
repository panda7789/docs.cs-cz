---
title: CLSID_RESOLUTION_FLAGS – výčet
ms.date: 03/30/2017
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
ms.openlocfilehash: d52f9f0bc2ff27d7849a80a424714aa84d3688fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136999"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="af6ca-102">CLSID_RESOLUTION_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="af6ca-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="af6ca-103">Obsahuje hodnoty, které určují, jak by měl modul CLR (Common Language Runtime) vyřešit `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="af6ca-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af6ca-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="af6ca-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af6ca-105">Members</span></span>  
  
|<span data-ttu-id="af6ca-106">Člen</span><span class="sxs-lookup"><span data-stu-id="af6ca-106">Member</span></span>|<span data-ttu-id="af6ca-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af6ca-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="af6ca-108">Označuje výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="af6ca-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="af6ca-109">Indikuje, že modul runtime vyhledává v registru a aplikuje zásady překrytí.</span><span class="sxs-lookup"><span data-stu-id="af6ca-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af6ca-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af6ca-110">Requirements</span></span>  
 <span data-ttu-id="af6ca-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af6ca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af6ca-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af6ca-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af6ca-113">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af6ca-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af6ca-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af6ca-114">See also</span></span>

- [<span data-ttu-id="af6ca-115">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="af6ca-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
