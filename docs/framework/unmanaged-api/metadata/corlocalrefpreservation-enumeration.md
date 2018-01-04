---
title: "CorLocalRefPreservation – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLocalRefPreservation
api_location: mscoree.dll
api_type: COM
f1_keywords: CorLocalRefPreservation
helpviewer_keywords: CorLocalRefPreservation enumeration [.NET Framework metadata]
ms.assetid: 44757163-1228-4213-a4c4-d4de503cc75d
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c35bbfef62f65a9a401d00f9ae56e2f4c00bb0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corlocalrefpreservation-enumeration"></a><span data-ttu-id="0d02e-102">CorLocalRefPreservation – výčet</span><span class="sxs-lookup"><span data-stu-id="0d02e-102">CorLocalRefPreservation Enumeration</span></span>
<span data-ttu-id="0d02e-103">Obsahuje hodnot příznaku pro zpracování místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="0d02e-103">Contains flag values for the treatment of local references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d02e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d02e-104">Syntax</span></span>  
  
```  
typedef enum CorLocalRefPreservation  
{  
    MDPreserveLocalRefsNone     =   0x00000000,  
    MDPreserveLocalTypeRef      =   0x00000001,  
    MDPreserveLocalMemberRef    =   0x00000002  
} CorLocalRefPreservation;  
```  
  
## <a name="members"></a><span data-ttu-id="0d02e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0d02e-105">Members</span></span>  
  
|<span data-ttu-id="0d02e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0d02e-106">Member</span></span>|<span data-ttu-id="0d02e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0d02e-107">Description</span></span>|  
|------------|-----------------|  
|`MDPreserveLocalRefsNone`|<span data-ttu-id="0d02e-108">Zachovat žádné místní odkazy.</span><span class="sxs-lookup"><span data-stu-id="0d02e-108">Preserve no local references.</span></span>|  
|`MDPreserveLocalTypeRef`|<span data-ttu-id="0d02e-109">Zachovejte místního typu odkazy.</span><span class="sxs-lookup"><span data-stu-id="0d02e-109">Preserve local type references.</span></span>|  
|`MDPreserveLocalMemberRef`|<span data-ttu-id="0d02e-110">Zachovejte odkazy na místní členy.</span><span class="sxs-lookup"><span data-stu-id="0d02e-110">Preserve local member references.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d02e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0d02e-111">Requirements</span></span>  
 <span data-ttu-id="0d02e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d02e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d02e-113">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0d02e-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0d02e-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d02e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d02e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d02e-115">See Also</span></span>  
 [<span data-ttu-id="0d02e-116">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="0d02e-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
