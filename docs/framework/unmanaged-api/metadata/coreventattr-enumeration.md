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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1a50c15071ea1e696e508c779309225c7e7bfa2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097818"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="8fdcc-102">CorEventAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="8fdcc-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="8fdcc-103">Obsahuje hodnoty, které popisují metadata událost.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fdcc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fdcc-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="8fdcc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8fdcc-105">Members</span></span>  
  
|<span data-ttu-id="8fdcc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8fdcc-106">Member</span></span>|<span data-ttu-id="8fdcc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fdcc-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="8fdcc-108">Určuje, že událost je speciální a který odpovídá názvu jak.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="8fdcc-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="8fdcc-110">Určuje, že modul common language runtime by měla kontrolovat kódování název události.</span><span class="sxs-lookup"><span data-stu-id="8fdcc-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8fdcc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fdcc-111">Requirements</span></span>  
 <span data-ttu-id="8fdcc-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fdcc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fdcc-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8fdcc-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="8fdcc-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8fdcc-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8fdcc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fdcc-115">See also</span></span>

- [<span data-ttu-id="8fdcc-116">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="8fdcc-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
