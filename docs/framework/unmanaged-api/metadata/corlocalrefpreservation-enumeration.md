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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045708"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="5a955-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="5a955-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="5a955-103">Obsahuje příznak hodnoty pro zacházení s místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="5a955-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a955-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a955-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="5a955-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5a955-105">Members</span></span>  
  
|<span data-ttu-id="5a955-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5a955-106">Member</span></span>|<span data-ttu-id="5a955-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5a955-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="5a955-108">Zachovat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="5a955-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="5a955-109">Zachovat místní typ reference.</span><span class="sxs-lookup"><span data-stu-id="5a955-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="5a955-110">Zachovat místní člen odkazy.</span><span class="sxs-lookup"><span data-stu-id="5a955-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a955-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a955-111">Requirements</span></span>  
 <span data-ttu-id="5a955-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a955-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a955-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="5a955-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5a955-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a955-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a955-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a955-115">See also</span></span>

- [<span data-ttu-id="5a955-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="5a955-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
