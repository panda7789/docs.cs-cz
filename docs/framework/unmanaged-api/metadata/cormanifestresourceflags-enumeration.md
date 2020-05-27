---
title: CorManifestResourceFlags – výčet
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: ebdff88e9fdf499b809d56c4c29a906dbef9ec40
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008973"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="66fec-102">CorManifestResourceFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="66fec-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="66fec-103">Určuje viditelnost prostředků kódovaných v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="66fec-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66fec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66fec-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="66fec-105">Členové</span><span class="sxs-lookup"><span data-stu-id="66fec-105">Members</span></span>  
  
|<span data-ttu-id="66fec-106">Člen</span><span class="sxs-lookup"><span data-stu-id="66fec-106">Member</span></span>|<span data-ttu-id="66fec-107">Description</span><span class="sxs-lookup"><span data-stu-id="66fec-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="66fec-108">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="66fec-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="66fec-109">Prostředky jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="66fec-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="66fec-110">Prostředky jsou soukromé.</span><span class="sxs-lookup"><span data-stu-id="66fec-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66fec-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66fec-111">Requirements</span></span>  
 <span data-ttu-id="66fec-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66fec-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66fec-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="66fec-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="66fec-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66fec-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fec-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="66fec-115">See also</span></span>

- [<span data-ttu-id="66fec-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="66fec-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
