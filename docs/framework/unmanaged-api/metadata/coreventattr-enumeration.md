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
ms.openlocfilehash: 7562ec10b6822ae0ec1478cdb077578493ea0b7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781884"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="b04fd-102">CorEventAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="b04fd-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="b04fd-103">Obsahuje hodnoty, které popisují metadata událost.</span><span class="sxs-lookup"><span data-stu-id="b04fd-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b04fd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="b04fd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b04fd-105">Members</span></span>  
  
|<span data-ttu-id="b04fd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b04fd-106">Member</span></span>|<span data-ttu-id="b04fd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b04fd-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="b04fd-108">Určuje, že událost je speciální a který odpovídá názvu jak.</span><span class="sxs-lookup"><span data-stu-id="b04fd-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="b04fd-109">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="b04fd-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="b04fd-110">Určuje, že modul common language runtime by měla kontrolovat kódování název události.</span><span class="sxs-lookup"><span data-stu-id="b04fd-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b04fd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b04fd-111">Requirements</span></span>  
 <span data-ttu-id="b04fd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b04fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04fd-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b04fd-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b04fd-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04fd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b04fd-115">See also</span></span>

- [<span data-ttu-id="b04fd-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b04fd-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
