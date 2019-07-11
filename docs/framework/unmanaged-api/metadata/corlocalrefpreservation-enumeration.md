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
ms.openlocfilehash: 6338034d6714e8770e06ff61994fdf4433eb1684
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781792"
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="53d33-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="53d33-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="53d33-103">Obsahuje příznak hodnoty pro zacházení s místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="53d33-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53d33-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="53d33-105">Členové</span><span class="sxs-lookup"><span data-stu-id="53d33-105">Members</span></span>  
  
|<span data-ttu-id="53d33-106">Člen</span><span class="sxs-lookup"><span data-stu-id="53d33-106">Member</span></span>|<span data-ttu-id="53d33-107">Popis</span><span class="sxs-lookup"><span data-stu-id="53d33-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="53d33-108">Zachovat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="53d33-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="53d33-109">Zachovat místní typ reference.</span><span class="sxs-lookup"><span data-stu-id="53d33-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="53d33-110">Zachovat místní člen odkazy.</span><span class="sxs-lookup"><span data-stu-id="53d33-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53d33-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53d33-111">Requirements</span></span>  
 <span data-ttu-id="53d33-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53d33-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53d33-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="53d33-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="53d33-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53d33-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d33-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53d33-115">See also</span></span>

- [<span data-ttu-id="53d33-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="53d33-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
