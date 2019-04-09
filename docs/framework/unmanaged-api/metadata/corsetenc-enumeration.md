---
title: CorSetENC – výčet
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fd903cb4a9ce664b7a1c958a3fef0c639d6845d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122314"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="6eec9-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="6eec9-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="6eec9-103">Obsahuje hodnoty použité k ovlivnění chování při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="6eec9-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eec9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eec9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6eec9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6eec9-105">Members</span></span>  
  
|<span data-ttu-id="6eec9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6eec9-106">Member</span></span>|<span data-ttu-id="6eec9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6eec9-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="6eec9-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="6eec9-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="6eec9-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="6eec9-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="6eec9-110">Označuje, že je možné aktualizovat metadata, tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="6eec9-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="6eec9-111">Označuje, že tokeny lze přesunout během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6eec9-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="6eec9-112">Označuje, že aktualizace může být tvořen pouze doplňky.</span><span class="sxs-lookup"><span data-stu-id="6eec9-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="6eec9-113">Tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="6eec9-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="6eec9-114">Označuje, že je přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="6eec9-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="6eec9-115">Označuje, že by se měla uložit tato metadata pouze změněné.</span><span class="sxs-lookup"><span data-stu-id="6eec9-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="6eec9-116">Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="6eec9-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6eec9-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eec9-117">Requirements</span></span>  
 <span data-ttu-id="6eec9-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eec9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eec9-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6eec9-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="6eec9-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6eec9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6eec9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eec9-121">See also</span></span>

- [<span data-ttu-id="6eec9-122">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="6eec9-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
