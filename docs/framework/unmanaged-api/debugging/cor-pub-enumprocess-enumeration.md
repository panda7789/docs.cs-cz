---
title: "COR_PUB_ENUMPROCESS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PUB_ENUMPROCESS
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_PUB_ENUMPROCESS
helpviewer_keywords: COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d92c484c8cb0142f59c26270674af73da5fbfa95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="ae70e-102">COR_PUB_ENUMPROCESS – výčet</span><span class="sxs-lookup"><span data-stu-id="ae70e-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="ae70e-103">Určuje typ procesu výčet.</span><span class="sxs-lookup"><span data-stu-id="ae70e-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae70e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae70e-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="ae70e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ae70e-105">Members</span></span>  
  
|<span data-ttu-id="ae70e-106">Název členu</span><span class="sxs-lookup"><span data-stu-id="ae70e-106">Member name</span></span>|<span data-ttu-id="ae70e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ae70e-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="ae70e-108">Spravované proces.</span><span class="sxs-lookup"><span data-stu-id="ae70e-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae70e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae70e-109">Remarks</span></span>  
 <span data-ttu-id="ae70e-110">Aktuální verze nespravovaného rozhraní API pro ladění zobrazí jenom spravovaných procesy.</span><span class="sxs-lookup"><span data-stu-id="ae70e-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae70e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae70e-111">Requirements</span></span>  
 <span data-ttu-id="ae70e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae70e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae70e-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ae70e-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ae70e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae70e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae70e-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae70e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae70e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae70e-116">See Also</span></span>  
 [<span data-ttu-id="ae70e-117">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="ae70e-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
