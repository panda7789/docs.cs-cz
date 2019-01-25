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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3d3ef78da9dd639d0f9050a8b61d1e365cd8b42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650246"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="2eb49-102">CorManifestResourceFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="2eb49-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="2eb49-103">Určuje, zda se prostředky kódovaný v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="2eb49-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eb49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2eb49-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="2eb49-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2eb49-105">Members</span></span>  
  
|<span data-ttu-id="2eb49-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2eb49-106">Member</span></span>|<span data-ttu-id="2eb49-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2eb49-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="2eb49-108">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="2eb49-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="2eb49-109">Prostředky jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="2eb49-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="2eb49-110">Prostředky jsou privátní.</span><span class="sxs-lookup"><span data-stu-id="2eb49-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2eb49-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2eb49-111">Requirements</span></span>  
 <span data-ttu-id="2eb49-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb49-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb49-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2eb49-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2eb49-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb49-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb49-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eb49-115">See also</span></span>
- [<span data-ttu-id="2eb49-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="2eb49-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
