---
title: "CorSetENC – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="dde14-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="dde14-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="dde14-103">Obsahuje hodnoty používané k ovlivnění chování při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="dde14-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dde14-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="dde14-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dde14-105">Members</span></span>  
  
|<span data-ttu-id="dde14-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dde14-106">Member</span></span>|<span data-ttu-id="dde14-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dde14-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="dde14-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="dde14-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="dde14-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="dde14-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="dde14-110">Označuje, že můžete aktualizovat metadata, nelze přesunout tokeny.</span><span class="sxs-lookup"><span data-stu-id="dde14-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="dde14-111">Označuje, že tokeny je možné přesouvat během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="dde14-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="dde14-112">Označuje, že aktualizace se může skládat pouze z dodatky.</span><span class="sxs-lookup"><span data-stu-id="dde14-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="dde14-113">Tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="dde14-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="dde14-114">Označuje, že je přírůstkové kompilace.</span><span class="sxs-lookup"><span data-stu-id="dde14-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="dde14-115">Označuje, že má být uložen aby pouze změněné metadata.</span><span class="sxs-lookup"><span data-stu-id="dde14-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="dde14-116">Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="dde14-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dde14-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dde14-117">Requirements</span></span>  
 <span data-ttu-id="dde14-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dde14-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dde14-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="dde14-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dde14-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dde14-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde14-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dde14-121">See Also</span></span>  
 [<span data-ttu-id="dde14-122">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="dde14-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
