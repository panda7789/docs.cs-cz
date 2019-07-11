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
ms.openlocfilehash: 2796be32154275387da891683cc5053095f534af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772323"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="185db-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="185db-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="185db-103">Obsahuje hodnoty použité k ovlivnění chování při generování metadat.</span><span class="sxs-lookup"><span data-stu-id="185db-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="185db-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="185db-105">Členové</span><span class="sxs-lookup"><span data-stu-id="185db-105">Members</span></span>  
  
|<span data-ttu-id="185db-106">Člen</span><span class="sxs-lookup"><span data-stu-id="185db-106">Member</span></span>|<span data-ttu-id="185db-107">Popis</span><span class="sxs-lookup"><span data-stu-id="185db-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="185db-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="185db-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="185db-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="185db-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="185db-110">Označuje, že je možné aktualizovat metadata, tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="185db-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="185db-111">Označuje, že tokeny lze přesunout během aktualizace.</span><span class="sxs-lookup"><span data-stu-id="185db-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="185db-112">Označuje, že aktualizace může být tvořen pouze doplňky.</span><span class="sxs-lookup"><span data-stu-id="185db-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="185db-113">Tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="185db-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="185db-114">Označuje, že je přírůstková kompilace.</span><span class="sxs-lookup"><span data-stu-id="185db-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="185db-115">Označuje, že by se měla uložit tato metadata pouze změněné.</span><span class="sxs-lookup"><span data-stu-id="185db-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="185db-116">Zahrnuje `MDUpdateENC`, `MDUpdateFull` a `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="185db-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="185db-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="185db-117">Requirements</span></span>  
 <span data-ttu-id="185db-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="185db-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185db-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="185db-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="185db-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185db-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185db-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="185db-121">See also</span></span>

- [<span data-ttu-id="185db-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="185db-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
