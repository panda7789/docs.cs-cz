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
ms.openlocfilehash: 93a194ea72ab894544927cf96304397b7211b5ac
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009155"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="9e7d6-102">CorSetENC – výčet</span><span class="sxs-lookup"><span data-stu-id="9e7d6-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="9e7d6-103">Obsahuje hodnoty, které slouží k ovlivnění chování během generování metadat.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e7d6-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9e7d6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9e7d6-105">Members</span></span>  
  
|<span data-ttu-id="9e7d6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9e7d6-106">Member</span></span>|<span data-ttu-id="9e7d6-107">Description</span><span class="sxs-lookup"><span data-stu-id="9e7d6-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="9e7d6-108">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="9e7d6-109">Zastaralé.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="9e7d6-110">Označuje, že je možné aktualizovat metadata, a tokeny nelze přesunout.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="9e7d6-111">Označuje, že tokeny lze během aktualizací přesunout.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="9e7d6-112">Označuje, že aktualizace mohou sestávat pouze z dodatků.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="9e7d6-113">Tokeny nejde přesunout.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="9e7d6-114">Indikuje, že je kompilace přírůstková.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="9e7d6-115">Indikuje, že se mají ukládat jenom změněná metadata.</span><span class="sxs-lookup"><span data-stu-id="9e7d6-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="9e7d6-116">Zahrnuje `MDUpdateENC` `MDUpdateFull` a `MDUpdateIncremental` .</span><span class="sxs-lookup"><span data-stu-id="9e7d6-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e7d6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e7d6-117">Requirements</span></span>  
 <span data-ttu-id="9e7d6-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e7d6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7d6-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="9e7d6-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9e7d6-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7d6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e7d6-121">See also</span></span>

- [<span data-ttu-id="9e7d6-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9e7d6-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
