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
ms.openlocfilehash: e4e4b9d9c7481bdc51aaf75b26b3805940875f8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442303"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="70a5f-102">CorEventAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="70a5f-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="70a5f-103">Obsahuje hodnoty, které popisují metadata události.</span><span class="sxs-lookup"><span data-stu-id="70a5f-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70a5f-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="70a5f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="70a5f-105">Members</span></span>  
  
|<span data-ttu-id="70a5f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="70a5f-106">Member</span></span>|<span data-ttu-id="70a5f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="70a5f-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="70a5f-108">Určuje, že událost je speciální a že její název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="70a5f-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="70a5f-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="70a5f-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="70a5f-110">Určuje, že by měl modul common language runtime kontrolovat kódování název události.</span><span class="sxs-lookup"><span data-stu-id="70a5f-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70a5f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70a5f-111">Requirements</span></span>  
 <span data-ttu-id="70a5f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70a5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70a5f-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="70a5f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="70a5f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70a5f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a5f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="70a5f-115">See Also</span></span>  
 [<span data-ttu-id="70a5f-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="70a5f-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
