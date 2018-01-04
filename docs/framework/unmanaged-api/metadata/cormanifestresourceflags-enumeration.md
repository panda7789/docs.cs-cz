---
title: "CorManifestResourceFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorManifestResourceFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorManifestResourceFlags
helpviewer_keywords: CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a1ad2aa505ba77f136a28b2cfa9f1fa357c37ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="97db9-102">CorManifestResourceFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="97db9-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="97db9-103">Určuje viditelnost prostředky v manifestu sestavení kódování.</span><span class="sxs-lookup"><span data-stu-id="97db9-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97db9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97db9-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="97db9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="97db9-105">Members</span></span>  
  
|<span data-ttu-id="97db9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="97db9-106">Member</span></span>|<span data-ttu-id="97db9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="97db9-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="97db9-108">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="97db9-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="97db9-109">Prostředky jsou veřejné.</span><span class="sxs-lookup"><span data-stu-id="97db9-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="97db9-110">Prostředky jsou soukromé.</span><span class="sxs-lookup"><span data-stu-id="97db9-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="97db9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97db9-111">Requirements</span></span>  
 <span data-ttu-id="97db9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97db9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97db9-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="97db9-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="97db9-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97db9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97db9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="97db9-115">See Also</span></span>  
 [<span data-ttu-id="97db9-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="97db9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
