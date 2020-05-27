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
ms.openlocfilehash: 42cb4e76bb77aebcee3b28035635a877513cdc04
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008986"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="43f71-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="43f71-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="43f71-103">Obsahuje hodnoty příznaků pro zpracování místních odkazů.</span><span class="sxs-lookup"><span data-stu-id="43f71-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43f71-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="43f71-105">Členové</span><span class="sxs-lookup"><span data-stu-id="43f71-105">Members</span></span>  
  
|<span data-ttu-id="43f71-106">Člen</span><span class="sxs-lookup"><span data-stu-id="43f71-106">Member</span></span>|<span data-ttu-id="43f71-107">Description</span><span class="sxs-lookup"><span data-stu-id="43f71-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="43f71-108">Neuchovávat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="43f71-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="43f71-109">Zachovat místní odkazy na typ.</span><span class="sxs-lookup"><span data-stu-id="43f71-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="43f71-110">Zachovat odkazy na místní členy.</span><span class="sxs-lookup"><span data-stu-id="43f71-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43f71-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43f71-111">Requirements</span></span>  
 <span data-ttu-id="43f71-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f71-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f71-113">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="43f71-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="43f71-114">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f71-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f71-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="43f71-115">See also</span></span>

- [<span data-ttu-id="43f71-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="43f71-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
