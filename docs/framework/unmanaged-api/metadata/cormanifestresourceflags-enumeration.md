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
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440707"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="68cbc-102">CorManifestResourceFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="68cbc-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="68cbc-103">Určuje viditelnost prostředky v manifestu sestavení kódování.</span><span class="sxs-lookup"><span data-stu-id="68cbc-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68cbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68cbc-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="68cbc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="68cbc-105">Members</span></span>  
  
|<span data-ttu-id="68cbc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="68cbc-106">Member</span></span>|<span data-ttu-id="68cbc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="68cbc-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="68cbc-108">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="68cbc-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="68cbc-109">Prostředky jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="68cbc-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="68cbc-110">Prostředky jsou soukromé.</span><span class="sxs-lookup"><span data-stu-id="68cbc-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68cbc-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68cbc-111">Requirements</span></span>  
 <span data-ttu-id="68cbc-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68cbc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68cbc-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="68cbc-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="68cbc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68cbc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68cbc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="68cbc-115">See Also</span></span>  
 [<span data-ttu-id="68cbc-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="68cbc-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
