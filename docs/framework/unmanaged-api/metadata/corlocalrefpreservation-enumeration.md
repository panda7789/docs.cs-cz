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
ms.openlocfilehash: e9ed3cdac726fbdbf9ee2b33f42565d8594bc36e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669676"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="e6dde-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="e6dde-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="e6dde-103">Obsahuje příznak hodnoty pro zacházení s místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="e6dde-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6dde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6dde-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="e6dde-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e6dde-105">Members</span></span>  
  
|<span data-ttu-id="e6dde-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e6dde-106">Member</span></span>|<span data-ttu-id="e6dde-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e6dde-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="e6dde-108">Zachovat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="e6dde-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="e6dde-109">Zachovat místní typ reference.</span><span class="sxs-lookup"><span data-stu-id="e6dde-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="e6dde-110">Zachovat místní člen odkazy.</span><span class="sxs-lookup"><span data-stu-id="e6dde-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6dde-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6dde-111">Requirements</span></span>  
 <span data-ttu-id="e6dde-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6dde-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6dde-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e6dde-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e6dde-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6dde-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dde-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6dde-115">See also</span></span>
- [<span data-ttu-id="e6dde-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="e6dde-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
