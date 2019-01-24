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
ms.openlocfilehash: bf1be8d5c709f3d6e5991e4d33dde2e923291a95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569411"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="4ed20-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="4ed20-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="4ed20-103">Obsahuje hodnoty použité k ovlivnění chování při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="4ed20-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ed20-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4ed20-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4ed20-105">Members</span></span>  
  
|<span data-ttu-id="4ed20-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4ed20-106">Member</span></span>|<span data-ttu-id="4ed20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4ed20-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="4ed20-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4ed20-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="4ed20-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4ed20-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="4ed20-110">Označuje, že je možné aktualizovat metadata, tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="4ed20-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="4ed20-111">Označuje, že tokeny lze přesunout během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="4ed20-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="4ed20-112">Označuje, že aktualizace může být tvořen pouze doplňky.</span><span class="sxs-lookup"><span data-stu-id="4ed20-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="4ed20-113">Tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="4ed20-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="4ed20-114">Označuje, že je přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="4ed20-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="4ed20-115">Označuje, že by se měla uložit tato metadata pouze změněné.</span><span class="sxs-lookup"><span data-stu-id="4ed20-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="4ed20-116">Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="4ed20-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ed20-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ed20-117">Requirements</span></span>  
 <span data-ttu-id="4ed20-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ed20-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed20-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4ed20-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4ed20-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed20-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed20-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ed20-121">See also</span></span>
- [<span data-ttu-id="4ed20-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="4ed20-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
