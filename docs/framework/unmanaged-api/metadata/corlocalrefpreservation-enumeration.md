---
title: CorLocalRefPreservation – výčet
ms.date: 03/30/2017
api_name:
- CorLocalRefPreservation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLocalRefPreservation
helpviewer_keywords:
- CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 845994b96445d8ec2a0e37affc5164b432894a91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102190"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="b61d9-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="b61d9-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="b61d9-103">Obsahuje příznak hodnoty pro zacházení s místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="b61d9-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b61d9-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="b61d9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b61d9-105">Members</span></span>  
  
|<span data-ttu-id="b61d9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b61d9-106">Member</span></span>|<span data-ttu-id="b61d9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b61d9-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="b61d9-108">Zachovat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="b61d9-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="b61d9-109">Zachovat místní typ reference.</span><span class="sxs-lookup"><span data-stu-id="b61d9-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="b61d9-110">Zachovat místní člen odkazy.</span><span class="sxs-lookup"><span data-stu-id="b61d9-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b61d9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b61d9-111">Requirements</span></span>  
 <span data-ttu-id="b61d9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61d9-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b61d9-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b61d9-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61d9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61d9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b61d9-115">See also</span></span>

- [<span data-ttu-id="b61d9-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b61d9-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
