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
ms.openlocfilehash: ec2972605c40f4ba292f5a5f58d6d3efed53f966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443555"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="6ad55-102">CorEventAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="6ad55-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="6ad55-103">Contains values that describe the metadata of an event.</span><span class="sxs-lookup"><span data-stu-id="6ad55-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ad55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ad55-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="6ad55-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6ad55-105">Members</span></span>  
  
|<span data-ttu-id="6ad55-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6ad55-106">Member</span></span>|<span data-ttu-id="6ad55-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6ad55-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="6ad55-108">Specifies that the event is special, and that its name describes how.</span><span class="sxs-lookup"><span data-stu-id="6ad55-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="6ad55-109">Reserved for internal use by the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="6ad55-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="6ad55-110">Specifies that the common language runtime should check the encoding of the event name.</span><span class="sxs-lookup"><span data-stu-id="6ad55-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ad55-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ad55-111">Requirements</span></span>  
 <span data-ttu-id="6ad55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ad55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ad55-113">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6ad55-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6ad55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ad55-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad55-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ad55-115">See also</span></span>

- [<span data-ttu-id="6ad55-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="6ad55-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
