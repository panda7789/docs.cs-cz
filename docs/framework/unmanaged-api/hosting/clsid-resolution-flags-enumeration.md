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
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616772"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="c049a-102">CLSID_RESOLUTION_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="c049a-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="c049a-103">Obsahuje hodnoty, které určují, jak by měl modul CLR (Common Language Runtime) vyřešit `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="c049a-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c049a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c049a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c049a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c049a-105">Members</span></span>  
  
|<span data-ttu-id="c049a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c049a-106">Member</span></span>|<span data-ttu-id="c049a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c049a-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="c049a-108">Označuje výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="c049a-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="c049a-109">Indikuje, že modul runtime vyhledává v registru a aplikuje zásady překrytí.</span><span class="sxs-lookup"><span data-stu-id="c049a-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c049a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c049a-110">Requirements</span></span>  
 <span data-ttu-id="c049a-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c049a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c049a-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c049a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c049a-113">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c049a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c049a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c049a-114">See also</span></span>

- [<span data-ttu-id="c049a-115">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="c049a-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
