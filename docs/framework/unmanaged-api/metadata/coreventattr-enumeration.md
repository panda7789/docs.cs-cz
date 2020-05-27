---
title: CorEventAttr – výčet
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
ms.openlocfilehash: e22b390271a7813dd1d34aecf5f8a62d7eb81005
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007432"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="36c61-102">CorEventAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="36c61-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="36c61-103">Obsahuje hodnoty, které popisují metadata události.</span><span class="sxs-lookup"><span data-stu-id="36c61-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36c61-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="36c61-105">Členové</span><span class="sxs-lookup"><span data-stu-id="36c61-105">Members</span></span>  
  
|<span data-ttu-id="36c61-106">Člen</span><span class="sxs-lookup"><span data-stu-id="36c61-106">Member</span></span>|<span data-ttu-id="36c61-107">Description</span><span class="sxs-lookup"><span data-stu-id="36c61-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="36c61-108">Určuje, že událost je zvláštní a že její název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="36c61-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="36c61-109">Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="36c61-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="36c61-110">Určuje, že modul CLR (Common Language Runtime) by měl kontrolovat kódování názvu události.</span><span class="sxs-lookup"><span data-stu-id="36c61-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36c61-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36c61-111">Requirements</span></span>  
 <span data-ttu-id="36c61-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c61-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c61-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="36c61-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="36c61-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c61-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="36c61-115">See also</span></span>

- [<span data-ttu-id="36c61-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="36c61-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
