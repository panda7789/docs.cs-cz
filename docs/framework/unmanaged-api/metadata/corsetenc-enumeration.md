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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045315"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="8d41f-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="8d41f-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="8d41f-103">Obsahuje hodnoty použité k ovlivnění chování při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="8d41f-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d41f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d41f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8d41f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8d41f-105">Members</span></span>  
  
|<span data-ttu-id="8d41f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8d41f-106">Member</span></span>|<span data-ttu-id="8d41f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8d41f-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="8d41f-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8d41f-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="8d41f-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8d41f-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="8d41f-110">Označuje, že je možné aktualizovat metadata, tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="8d41f-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="8d41f-111">Označuje, že tokeny lze přesunout během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="8d41f-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="8d41f-112">Označuje, že aktualizace může být tvořen pouze doplňky.</span><span class="sxs-lookup"><span data-stu-id="8d41f-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="8d41f-113">Tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="8d41f-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="8d41f-114">Označuje, že je přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="8d41f-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="8d41f-115">Označuje, že by se měla uložit tato metadata pouze změněné.</span><span class="sxs-lookup"><span data-stu-id="8d41f-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="8d41f-116">Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="8d41f-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d41f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d41f-117">Requirements</span></span>  
 <span data-ttu-id="8d41f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d41f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d41f-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8d41f-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8d41f-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d41f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d41f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d41f-121">See also</span></span>

- [<span data-ttu-id="8d41f-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8d41f-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
